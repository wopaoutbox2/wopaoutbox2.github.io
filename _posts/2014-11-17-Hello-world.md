---
layout: post
title: Test post
description: "Simple Introduction to TDD python"
tags: [ code]
comments: true
---
I'm currently running our second cohort for our Women in Passion programme and I would like to introduce TDD to my students in a painless way. I believe TDD allows developers to think through their problem before writing the actual solution. In this way, a developer will be forced to think of the design of her solution and the different possible routes. I tend to fall in the trap alot of writing no tests and coming up with a solution that solves the problem in one way and yet there's different possible routes(which takes us to the topic of [test coverage](http://www.thoughtworks.com/insights/blog/are-test-coverage-metrics-overrated)) . I have been victim to this several times after even after attending two talks on testing at a software thoughtworks.

I've learnt things tend to stick to my brain when I teach it to somebody , hopefully this works.

##For starters syntax for Unit Testing

The main methods that we make use of in unit testing for Python are:

* assert - base assert allowing you to write your own assertions
* assertEqual(a, b) - check a and b are equal
* assertNotEqual(a, b) - check a and b are not equal
* assertIn(a, b) - check that a is in the item b
* assertNotIn(a, b) - check that a is not in the item b
* assertFalse(a) - check that the value of a is False
* assertTrue(a) - check the value of a is True
* assertIsInstance(a, TYPE) - check that a is of type "TYPE"
* assertRaises(ERROR, a, args) - check that when a is called with args that it raises ERROR

##Next pip install nose 

nose is python unit testing package

##Next Example


{% highlight python linenos %}
#calculator.py
class Calculator(object):
 
    def add(self, x, y):
        pass
{% endhighlight %}


{% highlight python linenos %}
#testcalc.py
import unittest
from calculator import Calculator
 
class TddInPythonExample(unittest.TestCase):
 
    def test_calculator_add_method_returns_correct_result(self):
        calc = Calculator()
        result = calc.add(2,2)
        self.assertEqual(4, result)
if __name__ == '__main__':
    unittest.main()
{% endhighlight %}

Writing tests in python is pretty simple
Our code to be tested is in calculator.py and our tests in testcalc.py.
In testcalc.py,

* import the unittest module from python library

* we add a class to hold all out test cases

* the test method needs to to begin with "test_" which can be picked up nosetest runner for execution

When we run our tests we get a failed test at a particular line number.
<figure>
	<a href="http://lynnug.github.io/images/failed-test-1.png
"><img src="http://lynnug.github.io/images/failed-test-1.png
"></a>
	<figcaption><a href="http://lynnug.github.io/images/failed-test-1.png
" title="Failed test">Failed test</a>.</figcaption>
</figure>

lets edit our calculator.py and run our tests once more

{% highlight python linenos %}
#calculator.py
class Calculator(object):
 
    def add(self, x, y):
        return x+y
{% endhighlight %}

this is the result  of our test
<figure>
	<a href="http://lynnug.github.io/images/passed-test-1.png
"><img src="http://lynnug.github.io/images/passed-test-1.png
"></a>
	<figcaption><a href="http://lynnug.github.io/images/passed-test-1.png
" title="Failed test">Passed test</a>.</figcaption>
</figure>

Woop!! Woop!! , our test passed. However what if someone puts in strings instead of intergers. So we've gotten comfortable testing what the case we are currently interested in. Let's stir it up.

{% highlight python linenos %}
import unittest
from calculator import Calculator
class TddInPythonExample(unittest.TestCase):
   def setUp(self):
        self.calc = Calculator()
        
   def test_calculator_add_method_returns_correct_result(self):
    	self.result = self.calc.add(2,2)
    	self.assertEqual(4, self.result)
   def test_calculator_returns_error_message_if_both_args_not_numbers(self):
   		self.assertRaises(ValueError, self.calc.add,'two','three')


if __name__ == '__main__':
    unittest.main()

{% endhighlight %}

From the above code we have added a setUp function which aids in setting up our test object that will subsequently be used in our other tests. We have also added a test that checks for ValueError if strings are passed. Now lets run our tests.

<figure>
	<a href="http://lynnug.github.io/images/failed-test-2.png
"><img src="http://lynnug.github.io/images/failed-test-2.png
"></a>
	<figcaption><a href="http://lynnug.github.io/images/failed-test-2.png
" title="Failed test">Failed test</a>.</figcaption>
</figure>

Our one test fails because we fail to raise a ValueError, lets edit our calculator code to raise one.
{% highlight python linenos %}
class Calculator(object):
 
    def add(self, x, y):
        number_types = (int, long, float, complex)
 
        if isinstance(x, number_types) and isinstance(y, number_types):
            return x+y
        else:
            raise ValueError
{% endhighlight %}

From the above code you can see we do a check to see if x and y are numbers using isinstance. Now lets run our code. Below is our outcome.

<figure>
	<a href="http://lynnug.github.io/images/passed-test-2.png
"><img src="http://lynnug.github.io/images/passed-test-2.png
"></a>
	<figcaption><a href="http://lynnug.github.io/images/passed-test-2.png
" title="Failed test">Passed test</a>.</figcaption>
</figure>

That's simple example of testing using nose in python. Go forth and write more tests :)---
layout: post
title: "olivia's blog"
description: "This blog is about Olivia's WOPA journey"
tags: []

---


##THE WOMEN PASSION PROGRAM 2014
Enrolling for the first WOPA cohart is one of my achievements this year.Interacting and making friends with fellow girls with great minds and visions is simply owesome.
Being part of ateam which thinks and knows everything is possiple with technology is great and am loving it.

The sessions with Michael about self discovery introduced me to a whole new and exciting side of me,"determinig my own weather"
 Tina and Richard are simply owesome,they make me think that i can actually do business.

Now Lynns sessions are simply amazing.She makes difficult things look like a piece of cake.






