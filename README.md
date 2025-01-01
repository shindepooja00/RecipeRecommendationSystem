# Recipe Recommendation System

## Problem Statement
The goal of this project is to develop a system that recommends recipes based on user inputs and preferences. The system considers the following inputs to generate personalized recipe recommendations:

1. **User Preferences**:
   - Dietary restrictions (e.g., vegan, gluten-free).
   - Cuisine preferences (e.g., Italian, Mexican).
   - Past ratings (if available).
2. **Ingredients**:
   - Recipes are filtered and ranked based on the user's available ingredients.
3. **Constraints**:
   - Time to cook.
   - Difficulty level (easy, medium, hard).
   - Meal type (e.g., breakfast, lunch, dinner).

## Approach

### Overview
This project adopts a **content-based recommendation approach**, utilizing nutritional data and recipe ingredients to generate suggestions. The system leverages the following methods:

1. **Data Preprocessing**:
   - **TF-IDF Vectorization**: Extracts meaningful features from recipe ingredient lists.
   - **Standard Scaling**: Normalizes nutritional data (calories, fat, carbohydrates, etc.) to ensure uniformity.
   - **Feature Combination**: Merges text-based and numerical data into a single feature matrix.

2. **Recommendation Algorithm**:
   - **K-Nearest Neighbors (KNN)**: Identifies recipes most similar to the user’s input by calculating Euclidean distances in the combined feature space.
   - **Top-N Suggestions**: Returns the top 5 most relevant recipes based on similarity scores.

3. **Web Application**:
   - Built with **Flask** to provide a user-friendly interface for inputting preferences and displaying recommendations.

### Why This Approach?
- The **content-based method** ensures recommendations are generated purely based on the recipe’s attributes, avoiding dependency on historical user data.
- Using TF-IDF for ingredient analysis provides flexibility in understanding complex ingredient lists.
- The combined use of text and numerical features ensures more accurate and personalized recommendations.

---

## Challenges and Solutions

### Challenges
1. **Combining Heterogeneous Data**:
   - Ingredient data is text-based, while nutritional data is numerical. Merging these required careful feature engineering.
2. **Scalability**:
   - TF-IDF vectorization and KNN computations can be resource-intensive for large datasets.
3. **User Input Validation**:
   - Ensuring robust handling of invalid or missing input data.

### Solutions
1. **Feature Engineering**:
   - Used `StandardScaler` for numerical features and `TfidfVectorizer` for text data.
   - Combined the two into a single feature matrix using NumPy.
2. **Optimizing Computation**:
   - Limited the TF-IDF feature set to the top 500 terms to reduce dimensionality.
3. **Input Validation**:
   - Implemented error handling in the Flask app to guide users when invalid inputs are detected.

---

## Ideas for Improvement

1. **Hybrid Recommendation System**:
   - Combine content-based filtering with collaborative filtering to incorporate user feedback and ratings for better recommendations.

2. **Recipe Rating and Feedback**:
   - Add functionality for users to rate recipes, enabling a more dynamic and personalized experience over time.

3. **Advanced NLP Techniques**:
   - Use transformer models (e.g., BERT) for deeper understanding of ingredient semantics.

4. **Optimization for Large Datasets**:
   - Implement approximate nearest neighbor (ANN) algorithms (e.g., FAISS) for faster recommendations.

5. **Enhanced UI**:
   - Add features like recipe bookmarking, advanced filtering (by time or difficulty), and pagination.

---

## Example Queries

### Input Example:
- Calories: 500
- Fat: 20g
- Carbohydrates: 50g
- Protein: 30g
- Cholesterol: 50mg
- Sodium: 200mg
- Fiber: 5g
- Ingredients: "tomato, basil, mozzarella"
- Meal Type: Dinner
- Difficulty: Easy
- Dietary Restrictions: Vegetarian

### Output Example:
Top 5 recipe suggestions with:
- Recipe name.
- Short description (ingredients list).
- Preparation steps.
- Link to an image.

---

## Open-Source Libraries Used
1. **Flask**: For building the web interface.
2. **Pandas**: For data manipulation.
3. **NumPy**: For numerical computations.
4. **Scikit-learn**: For TF-IDF vectorization, scaling, and KNN model implementation.
5. **Bootstrap**: For styling the web interface.

---

## How to Run the Project
1. Clone this repository.
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Place the `recipes.csv` file in the root directory.
4. Run the Flask application:
   ```bash
   python app.py
   ```
5. Open your browser and navigate to `http://127.0.0.1:5000` to access the system.

---

## Conclusion
This project demonstrates a practical application of content-based recommendation systems using real-world recipe data. While effective, it leaves room for enhancement through hybrid methods, user feedback incorporation, and scalability optimizations.

