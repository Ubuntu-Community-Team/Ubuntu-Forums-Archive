---
title: "spreadsheet: convert time ranges in various formats into one uniform format"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by hanzj on 2009-10-28
Hello,
 
I have a spreadsheet in which one column has "time ranges".
The entries in this column vary in their formats. Here are some example cells from the column:
 
> 6:10 pm -7:25
6pm-7pm
1:52pm-3:25pm
7:30 am - 9 am

 
 
Is there a way to get these time ranges into one, uniform format?
What I had in mind was *HH:MM - HH:MM* format. For example:
 
>  
18:10-19:25
18:00-19:00
13:52-15:25
07:30-09:30

 
 
Thank you

---

### Post by SteveDee on 2009-10-30
I think you will need to use spreadsheet functions to do what you want to do, and suggest you start by separating the 2 times that make up the range into 2 separate cells. In your example, each range uses "-" as a separator so in my attached example I've used =FIND("-",ref,1) to locate its position.

Having got the times into am/pm format in col "I", its simple to use =TIMEVALUE(ref) to convert this to 24hr representation in col "J".

As you can see in my example, I have not dealt with spaces within the time string, but will leave you to figure out how to correct this.

I hope this helps.

---

