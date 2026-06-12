---
title: "openOffice calc formula question regarding &quot;&quot; marks"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by nachos99 on 2009-03-17
is there a way put in quotation marks within a formula?  that is, i would like to have the quotation marks show up in the result.

let's say A1=rock and A2=paper  and i want A3 to be: rock beats "paper."

A3=A1&" beats"&"A3"&"."  would just be: rock beats paper.  misisng the " " i need.

i read a suggestion of using triple quotes for excel, but """ did not appear to work.

thanks in advance,

---

### Post by LowSky on 2009-03-17
what is the formula trying to say?
is it this?
A1>A2, then rock beats paper

---

### Post by LowSky on 2009-03-17
I made a small spreedsheet of what I think your trying to accomplish

its just a simple If statement basically

A1= Rock
A2= Paper
A3= Rock beats paper
A4= Paper beats rock
then the formula
=(IF(B2>C2,A3,A4))

B2 and C2 being a number (for this exercise)


to get quotation marks just simple use the " marks twice, like so

""rock beats paper""

it will show up as "rock beats paper"
_______________________

---

