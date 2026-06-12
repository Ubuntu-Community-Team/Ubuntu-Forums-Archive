---
title: "How do I search a pair of numbers in Openoffice Calc?"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Saubazi on 2011-02-05
I think with Excel it could work with match(B1&C1,B1:B20&C1:C20)
but it does not seem to work with openoffice...

The problem is I have two columns and numbers may appear duplicate
and I want to find the right combination and get the row number or so.

For example 
Column A    Column B
1           2
1           3
1           4
2           2
2           3
2           4

I would like to find for example ro for pair 2 and 2

One solution seems to be making third column with =A1&"_"&B1
and then looking with =match(A1&"_"&B1;C1:C20)
Openoffice does not seem to like combining the two columns into an array with B1:B20&C1:C20

---

### Post by TeoBigusGeekus on 2011-02-05
It doesn't actually solve your problem with the match function, but if you bother to create a third column, why not give its value as
```
=if(b1=c1,1,0)
```
drag it all the way down to the end of your data and then autofilter this column searching for 1?

---

### Post by hashimoto on 2011-02-05
> **Saubazi said:**
> I think with Excel it could work with match(B1&C1,B1:B20&C1:C20)
but it does not seem to work with openoffice...

The problem is I have two columns and numbers may appear duplicate
and I want to find the right combination and get the row number or so.

For example 
Column A    Column B
1           2
1           3
1           4
2           2
2           3
2           4

I would like to find for example ro for pair 2 and 2

One solution seems to be making third column with =A1&"_"&B1
and then looking with =match(A1&"_"&B1;C1:C20)
Openoffice does not seem to like combining the two columns into an array with B1:B20&C1:C20

Howabout this:
Add column C and to each row in it formula =IF(Ax=Bx)
Then in any cell formula =MATCH(1;C1:Cx;0)
Gives you the first row number with duplicate or N/A if not found.

---

### Post by Saubazi on 2011-02-08
I think you both misunderstood. I have two columns with IDs A and B (they stand for different things) and in my table there are also more columns. I am searching for a correct combination of ID from column A and one from column B - this means that I want to create a more condensed table.

Maybe like this:
A       B       C
1       1      55
1       2      11
1       4      22
1      11     456
2       1      11
2       5      10
2       2      11



And then I would make a search table
A       B      C
1       4      here then with match the row where combination 1 in column A and simultaneously 4 in column B - the answer would be 3

---

### Post by hashimoto on 2011-02-09
Try looking OOo helpfile (F1) and search for DGET. That should be something in line of what you are looking for.

---

