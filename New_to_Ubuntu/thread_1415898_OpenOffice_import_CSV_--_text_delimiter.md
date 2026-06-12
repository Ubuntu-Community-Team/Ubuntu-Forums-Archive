---
title: "OpenOffice import CSV -- text delimiter"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by mathfreak123 on 2010-02-25
So, I've been able to import CSV files into OpenOffice Spreadsheet **almost** nicely. The one issues I found that is troubling is that when I import numbers, a single quote appears in front of every number in every cell.

I could fix this by finding and replacing all the quotes with an empty string, but I'm wondering if anyone else had this problem (plus, I don't know where I would report this).

EDIT: Also, by playing around randomly with the delimiter options, I was able to import without the single quote appearing. However, I don't think I want to rest easy about it. :p

---

### Post by RedDog1 on 2010-02-25
> **mathfreak123 said:**
> So, I've been able to import CSV files into OpenOffice Spreadsheet **almost** nicely. The one issues I found that is troubling is that when I import numbers, a single quote appears in front of every number in every cell.
 
I could fix this by finding and replacing all the quotes with an empty string, but I'm wondering if anyone else had this problem (plus, I don't know where I would report this).
 
EDIT: Also, by playing around randomly with the delimiter options, I was able to import without the single quote appearing. However, I don't think I want to rest easy about it. :p
 
Is Calc then treating the numbers as text? I ask, because that is how you tell excel to treat numbers & symbols as text. For example, if you typed =a1+b1+c1 in a cell in excel, it would execute that formula. Now, if you typed '=a1+b1+c1 in a cell, it would show the formula without executing it. The ' tells excel to treat the contents of that cell as text, regardles of what is typed after the ' in the cell. Hve you tried highlighting a range of cells, choosing find & replace, typing ' in the find box, and leaving the replace box empty? I should delete all the ' marks within the range, if Calc has that option.
 
I am still learning the OpenOffice programs, but I do know excel fairly well. I hope that helped.

---

### Post by mathfreak123 on 2010-02-25
> **RedDog1 said:**
> Is Calc then treating the numbers as text? I ask, because that is how you tell excel to treat numbers & symbols as text. For example, if you typed =a1+b1+c1 in a cell in excel, it would execute that formula. Now, if you typed '=a1+b1+c1 in a cell, it would show the formula without executing it. The ' tells excel to treat the contents of that cell as text, regardles of what is typed after the ' in the cell. Hve you tried highlighting a range of cells, choosing find & replace, typing ' in the find box, and leaving the replace box empty? I should delete all the ' marks within the range, if Calc has that option.
 
I am still learning the OpenOffice programs, but I do know excel fairly well. I hope that helped.

Yes, I was able to remove all the quotes in the fashion you described. Glad to know that's how the program tells text apart from numbers. :D

Is there an option to not having the program treat the numbers as text other than the find & replace method? If you only know how to do so in Excel, that would be fine as well; I'll just try to find an OpenOffice equivalent. :p

---

### Post by RedDog1 on 2010-02-25
> **mathfreak123 said:**
> Yes, I was able to remove all the quotes in the fashion you described. Glad to know that's how the program tells text apart from numbers. :D
 
Is there an option to not having the program treat the numbers as text other than the find & replace method? If you only know how to do so in Excel, that would be fine as well; I'll just try to find an OpenOffice equivalent. :p
 
Have you tried going into format cells, and choosing number instead of text?  That is the only thing that comes to mind at the moment without playing around with the data myself.

---

### Post by mathfreak123 on 2010-02-25
> **RedDog1 said:**
> Have you tried going into format cells, and choosing number instead of text?  That is the only thing that comes to mind at the moment without playing around with the data myself.

I don't believe there is an option in format cells (or one that I found). However, I remember that you can (de)select "Quoted fields as text" under the delimiter options while importing.:D

---

### Post by RedDog1 on 2010-02-25
> **mathfreak123 said:**
> I don't believe there is an option in format cells (or one that I found). However, I remember that you can (de)select "Quoted fields as text" under the delimiter options while importing.:D
 
I was referring to formatting cells in Calc, not during importing. Does that make sense?

---

### Post by mathfreak123 on 2010-02-25
> **RedDog1 said:**
> I was referring to formatting cells in Calc, not during importing. Does that make sense?

Yeah, that's where I looked. I did not find anything of interest.

---

### Post by RedDog1 on 2010-02-25
> **mathfreak123 said:**
> Yeah, that's where I looked. I did not find anything of interest.
 
 
I will have to look around then, and let you know what I find.

---

### Post by mathfreak123 on 2010-02-25
> **RedDog1 said:**
> I will have to look around then, and let you know what I find.

Sounds great! Thank you for your time!

I'm able to work on my data in the meantime.

---

### Post by gesualdo.antani on 2010-04-26
> **mathfreak123 said:**
> So, I've been able to import CSV files into OpenOffice Spreadsheet **almost** nicely. The one issues I found that is troubling is that when I import numbers, a single quote appears in front of every number in every cell.

I could fix this by finding and replacing all the quotes with an empty string

I can't do this as the search function can't find the quotes. Also, no option in format cell seems to be useful to get rid of the quotes. Somebody has an alternative workaround?

---

### Post by The Cog on 2010-04-26
I can't seem to produce this. Can you perhaps post the first 5 lines from a spreadsheed where you're having this trouble, assuming it's not confidential info?

---

### Post by mathfreak123 on 2010-04-26
> **gesualdo.antani said:**
> I can't do this as the search function can't find the quotes. Also, no option in format cell seems to be useful to get rid of the quotes. Somebody has an alternative workaround?

Have you tried updating OpenOffice?

> **The Cog said:**
> I can't seem to produce this. Can you perhaps post the first 5 lines from a spreadsheed where you're having this trouble, assuming it's not confidential info?

I'm not sure which post The Cog is referring, too, so I'll just assume it's my problem.

I don't remember clearly what file it was, but I think the lines appeared as follows:

```
"Project: ,""Scanner 2.0"""
"Description: ,""Temperature Scanning for the Keithley 199 DMM/Scanner"""
"Owner: ,""K Street Technology Center"""
"Created: ,""Thursday, February 18, 2010, 5:53:58 pm"""

COMMENTS

DMM SETTINGS
"DMM Status String: ,""1990204000023010000001010000000001"""
"Function: ,""DC Volts"""
"Range: ,""300 mV"""
"Resolution: ,""4œ digits"""

SAMPLING PARAMETERS
"Sampling Period: ,""1"","" seconds"""
"Sampling Interval: ,""3000"","" seconds"""
"Channels Sampled: ,""3"""
"Estimated Duration: ,""0:50:00"""
"Estimated Samples: ,""3002"""

UNITS
"Temperature: ,""°C"""
"Time: ,""seconds"""

GRAPH TITLES
"Title: ,""Scanner 2.0"""
"Subtitle: ,""Temperature Scanning for the Keithley 199 DMM/Scanner"""
"Identification: ,""K Street Technology Center"""

SCANNER DATA
"Channel Number,""1"",""2"",""3"""
"Thermocouple Type,""Type J Thermocouple"",""Type J Thermocouple"",""Type J Thermocouple"""
"Channel Name,""Channel 1"",""Channel 2"",""Channel 3"""			
0	20.55	20.16	39.1
1.22	20.03	19.51	-124.7
2.22	20.29	20.03	-182.52
3.22	20.16	19.77	-182.52
4.22	20.16	19.64	-182.52
5.22	20.16	19.9	-182.52
6.22	20.16	19.77	-171.79
7.22	20.03	19.64	-102.26
8.22	19.9	19.64	-62.26
9.22	19.9	19.77	-3.68
10.22	19.77	19.64	20.29
11.22	19.9	19.77	-98.42
12.22	19.9	19.77	89.71
13.22	19.77	19.51	6.99
14.22	19.9	19.77	113.56
15.22	19.77	19.51	95.55
16.22	19.77	19.64	154.85
17.22	19.77	19.77	123.5
18.22	19.9	19.77	130.35
19.22	19.9	19.77	276.27
20.22	19.9	19.77	299.97
21.22	19.9	19.64	139.63
22.22	20.03	19.77	309.21
23.22	19.9	19.77	212.77
24.22	20.03	19.9	423.82
25.22	20.16	19.77	455.65
26.22	20.16	19.77	446.07
27.22	20.29	19.77	388.23
28.22	20.29	19.77	453.95
29.22	20.42	19.77	390.67
30.22	20.29	19.77	376.27
31.22	20.55	19.77	434.29
32.22	20.55	19.64	313.23
33.22	20.68	19.9	363.09
34.22	20.68	19.63	607.78
35.22	27.72	19.77	492.95
36.22	241.95	20.03	310.43
37.22	282.22	19.9	230.21
38.22	293.03	20.03	216.28
39.22	296.32	19.9	131.7
40.22	297.17	20.03	39.1
41.22	296.57	19.64	4.33
42.22	295.7	20.03	31.61
```

The data runs on after that. I notice that the data values don't have quotes around them, yet the values have quotes around them in the other files. Perhaps this is what caused OpenOffice to trip? The question I really have then is how I would remove the single quotes in each of the cells without using search and replace (which I consider to be somewhat....forceful).

---

### Post by The Cog on 2010-04-27
Actually, I was assuming that the original Feb conversation was dead so I was answering the recent question. Not that it matters.

That's not exactly a CSV file you posted there. I made a quick change to it to make it import better - give it a try and see if that does what you want. It removes all quotes from the file, and replaces all sequences of two or more spaces with a comma. The following command assumes that x.csv is the original file, and creates x2.csv.
```
sed -r -e 's/  +/,/g' -e 's/"//g' x.csv > x2.csv
```

Edit. Note the two spaces before the + sign. I've changed from quote tags to code tags because the forum was compressing the two spaces into one.

---

### Post by mathfreak123 on 2010-04-27
> **The Cog said:**
> Actually, I was assuming that the original Feb conversation was dead so I was answering the recent question. Not that it matters.

That's not exactly a CSV file you posted there. I made a quick change to it to make it import better - give it a try and see if that does what you want. It removes all quotes from the file, and replaces all sequences of two or more spaces with a comma. The following command assumes that x.csv is the original file, and creates x2.csv.
```
sed -r -e 's/  +/,/g' -e 's/"//g' x.csv > x2.csv
```

Edit. Note the two spaces before the + sign. I've changed from quote tags to code tags because the forum was compressing the two spaces into one.

Thanks! This works for me.

---

### Post by The Cog on 2010-04-28
> **mathfreak123 said:**
> Thanks! This works for me.
Oh good.
If you prefer, sed can do an in-place edit rather than creating a new file. I didn't show you that earlier because you don't want to go mangling the original files until you're sure the mangling works properly. The way to do an in-place edit is like this:
```
sed -i -r -e 's/  +/,/g' -e 's/"//g' x.csv
```

---

