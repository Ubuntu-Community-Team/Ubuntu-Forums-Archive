---
title: "Regression analysis?"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by Tacowingnut on 2011-09-08
I changed to Libre Office a little while ago and I have a question about Calc.

I am a college senior and several times, I'm to do a regression analysis on data collected.
Since I've used Libre Office, however, I have no idea how to do that. I've looked it up on the "Help" page it provides, but it isn't very specific. Maybe I'm not looking right.

The question I want to ask is this; Is there a way I can get a neat little "Summary Output" like I did in Excel here on Calc? Any help would be appreciated.

Thank you.

---

### Post by haqking on 2011-09-08
> **Tacowingnut said:**
> I changed to Libre Office a little while ago and I have a question about Calc.

I am a college senior and several times, I'm to do a regression analysis on data collected.
Since I've used Libre Office, however, I have no idea how to do that. I've looked it up on the "Help" page it provides, but it isn't very specific. Maybe I'm not looking right.

The question I want to ask is this; Is there a way I can get a neat little "Summary Output" like I did in Excel here on Calc? Any help would be appreciated.

Thank you.


3 part tutorial here [http://www.openofficetips.com/blog/archives/2005/04/regression_anal.html](http://www.openofficetips.com/blog/archives/2005/04/regression_anal.html)

it is for openoffice calc, but they both work pretty much the same, they recently forked thats all ;-)

---

### Post by ajgreeny on 2011-09-08
It might also be worth having a look at gnumeric.  Open it up, go to Tools ->Statistical analysis ->Regression and see what that offers.  You may also need gnumeric-plugins-extra but I'm not sure.

---

### Post by meh_phistopheles on 2011-09-08
i don't know about libre office, and i'm not going to google search it for you, but off the top of my head i know that R is something you could use. you could use libre office calc to export your data to tab separated variables (TSV format), load the data to R, then run whatever command outputs regression.

---

### Post by Tacowingnut on 2011-09-08
> **ajgreeny said:**
> It might also be worth having a look at gnumeric.  Open it up, go to Tools ->Statistical analysis ->Regression and see what that offers.  You may also need gnumeric-plugins-extra but I'm not sure.
YES!
Thank you! With Gnumeric, I can pull out what I need no problem! \\:D/

---

### Post by haqking on 2011-09-08
> **Tacowingnut said:**
> YES!
Thank you! With Gnumeric, I can pull out what I need no problem! \\:D/

cool, remember to use thread tools to mark as solved so it helps others searching for solutions.

cheers

---

### Post by Old_Grey_Wolf on 2011-09-08
> **Tacowingnut said:**
> YES!
Thank you! With Gnumeric, I can pull out what I need no problem! \\:D/

I've been monitoring this thread hoping someone could provide an answer. I have booted Windows to do regression analysis in excel. The Gnumeric output is similar to what I am accustom to in excel.

---

### Post by SeijiSensei on 2012-07-04
I've resuscitated this thread because it was the first one I came across when trying to figure out how to run regressions in LibreOffice.  It looks like the answer is that you cannot.  However I thought I should mention two useful programs from the GNU project:

gretl - an extremely powerful econometrics package
gretl includes algorithms to estimate a wide variety of models besides simple ordinary least squares like logit and probit, simultaneous equations estimation with instrumental variables, nonlinear least squares, and other maximum-likelihood methods.

pspp - an open-source clone of the popular statistical package SPSS
pspp will read and write SPSS system files and adds a wide variety of other univariate and multivariate methods like crosstabulation, ANOVA, and the like.

Both these programs are available from the repositories.

---

