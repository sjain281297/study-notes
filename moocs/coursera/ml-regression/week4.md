# Week 4

* Symptom of overfitting:
	* When model is extremely overfit, magnitude of coefficients can be extremely large.

* Overfitting not unique to polynomial regression: can also occur if you have lots of inputs.

* Number of observations can influence overfitting:
	* Few observations (N small) can cause model to be rapidly overfit as complexity grows.
	* Many observations (N very large) can be harder to overfit (but harder to find datasets).

	<img src="./images/number-of-observations.png></img>

* The larger the inputs, the more change of data not including inputs for all data points causing overfitting.

* Balancing fits and magnitude of coefficients:
	* Can improve quality metric by factoring in coefficient magnitude to avoid complex models.
	* ``Total cost = measure of fit (RSS) + measure of coefficient magnitudes``.
	* Want to find the ideal balance between the two.
	* Ways to measure coefficient magnitude:
		* Add coefficients: $$ \hat{w}_0 + \hat{w}_1 ... \hat{w}_d $$
			* the negative coefficients would cancel out the others.
		* Add the abs value of coefficients: $$ \sum\limits_{i=0}^{D} | \hat{w}_i | $$
			* Aka "L1 norm"
		* Sum squared values of coefficients: $$ \sum\limits_{i=0}^{D} (\hat{w}_i)^2 $$ (sum of squared values of coefficients)
			* Aka "L2 norm"

* Resulting ridge objective and its extreme solution.
	* Can use an extra parameter to tune how much weight is applied to the measure of coefficient magnitude: $$ RSS(\mathbf{w}) + \lambda ||\mathbf{w}||_2^2 $$
	* Set the param to 0 = only RSS would weight in quality metric.
	* Set the param to $$ \infty $$, $$\mathbf{w} = 0 $$ would be the solution.
	* Need to find a balance between the two: enter "ridge regression" (aka $$ L_2 $$ regularisation.

* How ridge regression balances bias and variance.
	* High $$ \lambda $$ = high bias, low variance.
		* As $$ \lambda $$ get closer to infinitely, coefficients get smaller and less general.
	* Low  $$ \lambda $$ = low bias, high variance.
		* As $$ \lambda $$ get closer to 0, coefficients get larger (RSS takes over) and shit gets crazy.