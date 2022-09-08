# Book-recommendation

The project's objective was to create different book recommendation systems based on user-item rating data.

At first the users, books and ratings data were stored in MySQL database on the local server. A connection was set up to fetch the data in the python workspace. Thorough data cleaning was performed by removing irrational data corresponding to the year of publication and the age of the customers. Rating data were subdivided into implicit and explicit ratings. In the first model, the books were recommended based on their popularity which only considers the aggregate of the books' explicit ratings and not the customers’ data. 

In the second approach, Collaborative filtering based recommendation was employed. In order to save computational resources, only the users who have given at least 100 ratings and books which have received aggregated 100 or more ratings were considered for the modelling. This reduces the sparsity in the user-item rating matrix and improves the prediction. For each user, the nearest neighbours are determined using the NearestNeighbours module in sklearn. These neighbours can be sorted based on the similarity (1 – distance). Some users (pessimistic) may generally give bad ratings to all the books and some users (optimistic) may give good ratings to all the books. To compensate for the rating bias of such users the weighted sum of the difference between specific book rating and the mean rating of all books was considered. Based on this, the top 10 books for each user were predicted.

In the third approach, the LightFM model was used for the recommendation. The user-item rating matrix was split into train and test datasets and then converted to a co-ordinate matrix. LightFM model takes the user-item rating co-ordinate matrix and decompose/factorize it into two separate user and book embedding matrix. During the training process, the dot product between the embedded user and item matrix gives the rating predictions, which can then be used to find the error from the actual ratings. The final predicted ratings was then used for finding the recommended books. In addition, the model is also used to find the recommended users for a specific book. This can be advantageous for personalized marketing. The book embedding matrix after user-item rating matrix factorization was also be used to find similar books by using cosine similarity between the items. This can be used for suggesting the bought together books to the customers.

