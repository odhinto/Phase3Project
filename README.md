<h1 align="center">Hi 👋, I;m Anthony Odhiambo  </h1>

Github Repository: [Click to Open the Project Github Repository](https://github.com/odhinto/Phase3Project.git)

Tableau Dashboard: [Click to Open the Tableau Dashboard](https://public.tableau.com/views/MovieData_17378656876300/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)


# **Data Understanding**

Like most telecommunication companies, customer retention remains a critical challenge for **SyriaTel**. This is because as acquiring new customers is often more expensive than keeping existing ones. SyriaTel is experiencing customer churn where users discontinue their service. Identifying the patterns and factors that drive churn can help the company take proactive measures to reduce customer loss, enhance loyalty, and increase revenue.

The **primary objective** of this exercise is to leverage historical customer data with an aim to uncover key factors that predict churn

* Build a predictive model that accurately identifies customers at risk of churning
* Optimize model performance using feature engineering and tuning.

## **Dataset Overview**

The dataset has a mix of categorical data and numerical data. These can be summarized as follows:
**Customer Information**
* state - The U.S. state where the customer resides.
* account length - The number of days the customer has had an active account with SyriaTel.
* area code - The area code of the customer's phone number.
* phone number - The customer’s unique phone number (not useful for analysis and usually dropped).

**Subscription Plans**
* international plan - Indicates whether the customer has an international calling plan (yes or no).
* voice mail plan - Indicates whether the customer has a voicemail plan (yes or no).

**Usage Metrics**
* number vmail messages - The number of voicemail messages the customer has received.
* total day minutes - The total number of minutes the customer has spent on calls during the daytime.
* total day calls - The total number of calls made during the daytime.
* total day charge - The total charges incurred for calls made during the daytime.
* total eve minutes - The total number of minutes the customer has spent on calls during the evening.
* total eve calls - The total number of calls made during the evening.
* total eve charge - The total charges incurred for calls made during the evening.
* total night minutes - The total number of minutes the customer has spent on calls during the nighttime.
* total night calls - The total number of calls made during the nighttime.
* total night charge - The total charges incurred for calls made during the nighttime.
* total intl minutes - The total number of minutes the customer has spent on international calls.
* total intl calls - The total number of international calls made.
* total intl charge - The total charges incurred for international calls.


The task is to use these features to accurately predict customer churn.

### Data Understanding

<div align="center">
    <img src="pictures/movie_data_erd.jpeg" alt="Database Schema" width="800">
    <p><em>Movie Database Schema</em></p>
</div>

The movie database contains the following tables with shown columns:

*   **principals**: The principals table details main people (using their person_id)that were involved with different movies (using the movie_id) and the capacities in which they were involved e.g. director, actor, producer etc. There could be a relationship between these people and the success of the movie in the box office.

    ![image](https://github.com/user-attachments/assets/ffd68c86-7102-4032-860d-85dd3800fab2)
*   **persons**: The persons table details the name, birth year, death year and primary professions of the various people using their person_id. There could be a relationship between the people involved in a movie and the success of the movie in the box office.

    ![image](https://github.com/user-attachments/assets/66ac232a-c0fb-4b79-a8da-59e75efc6ced)
*   **known_for**: Known_for table details the various movies different people are known for by person_id and movie_id.

    ![image](https://github.com/user-attachments/assets/5bebda41-1b18-483f-ac93-8002a63c8226)
*   **directors**: Directors table details the various movies and the people they are known for by movie_id and person_id. There could be a relationship between the directors of a movie and the success of the movie in the box office.

    ![image](https://github.com/user-attachments/assets/a30f8dde-24ef-44b3-89a5-9a6da837a707)


*   **writers**: Writers table details the various movies and their pewriters by movie_id and person_id. There could be a relationship between the writers of a movie and the success of the movie in the box office.

    ![image](https://github.com/user-attachments/assets/49ace174-b171-4182-83b1-e8b2e8244d5a)
*   **movie_basics**: Movie_basics table details the various movie titles, the year they were released, the run-time minutes and the various genres (there may be need for feature engineering around this aspect). There could be a relationship between these parameters and the success of a movie in the box office.
![image](https://github.com/user-attachments/assets/b491a681-e270-4208-a14c-83f8ddce34b8)
*   **movie_ratings**: This table shows the average rating for each movie by movie_id and also the number of votes it received (which could give insight into how many people watched it??). There could be a relationship between these parameters and the success of a movie in the box office.

    ![image](https://github.com/user-attachments/assets/f67cf198-7561-4816-bfb9-c9a05a7018a0)
*   **movie_akas**: This table shows other movie features e.g. the region, language, type and attributes. There could be a relationship between these features and the success of a movie in the box office.
    ![image](https://github.com/user-attachments/assets/b0070954-a043-40bc-9291-73a28be69b40)

# **Exploratory Data Analysis**

We used Tableau to explore the data and established the following insights:


1. **Average Rating Per Genre:**

   Musical, Fantastical and Sci-Fi Genres registered the highest incidence among the top rated genres
    <div align="center">
        <img src="pictures/Average Rating By Genre.png" alt="average rating by genre" width="800">
        <p><em>Average Rating By Genre</em></p>
    </div>
2. **Popularity by Genre:**

    Fantasy, Action and Adventure Genres Feature Frequently on the Popularity Meter
    <div align="center">
        <img src="pictures/Popularity by Genre.png" alt="popularity by genre" width="800">
        <p><em>Popularity By Genre</em></p>
    </div>

3. **Average Profitability by Gentre:**

    Family, Horrors and Thrillers Register High Profitability i.e. profitability = (grossing/production budget) x 100%
   <div align="center">
        <img src="pictures/Average Profitability by Genre.png" alt="average profitability by genre" width="800">
        <p><em>Average Profitability By Genre</em></p>
    </div>

4. **Casting Insights:**

    The following are the highest grossing **actors** who consistently attract larger audiences:
    <div align="center">
        <img src="pictures/actors.PNG" alt="highest grossing actors" width="800">
        <p><em>Highest Grossing Actors</em></p>
    </div>

     The following are the highest grossing **actresses** who consistently attract larger audiences:
    <div align="center">
        <img src="pictures/actresses.PNG" alt="highest grossing actresses" width="800">
        <p><em>Highest Grossing Actresses</em></p>
    </div>

     The following are the highest grossing **directors** who consistently attract larger audiences:
    <div align="center">
        <img src="pictures/directors.PNG" alt="image3" width="800">
        <p><em>Highest Grossing Directors</em></p>
    </div>

     The following are the highest grossing **producers** who consistently attract larger audiences:
    <div align="center">
        <img src="pictures/producers.PNG" alt="image2" width="800">
        <p><em>Highest Grossing Producers</em></p>
    </div>

    The following are the highest grossing **writers** who consistently attract larger audiences:
    <div align="center">
        <img src="pictures/writers.PNG" alt="image1" width="800">
        <p><em>Highest Grossing Writers</em></p>
    </div>
5. **Average Production Budget vs Average Profitability by Genre:**

  

# **Conclusion**

1. **Genre Focus:**
   - Focus on highly rated genres 

2. **Director and Writer Partnerships:**
   - Invest in partnerships with proven directors and writers to enhance the likelihood of success.

3. **Casting Strategy:**
   - Include at least one A-list actor in high-budget projects while ensuring strong scripts and storytelling to retain audience satisfaction.

5. **Budget Allocation:**
   - Focus on low- to mid-budget films with a clear emphasis on maximizing profit margins.

6. **Long-Term Strategy:**
   - Continuously analyze audience preferences and emerging trends to adapt to shifting market demands.


    
# **Recommendation**
These recommendations provide a roadmap for achieving consistent profitability and success in the competitive movie industry.   Among the top 30 most expensive movies, Family, Fantasy, Musicals yield the highest profitability at relatively low budget.

 <div align="center">
        <img src="pictures/Average Production Budget vs Average Profitability by Genre.png" alt="new image" width="800">
        <p><em>Average Production Budget vs Average Profitability by Genre</em></p>
    </div>


For a start, our company should focus on producing this genre.


Average Production Budget vs Average Profitability by Genre