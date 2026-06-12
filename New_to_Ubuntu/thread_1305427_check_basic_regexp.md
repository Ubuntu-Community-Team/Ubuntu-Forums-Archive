---
title: "check basic regexp"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by pankajphartiyal on 2009-10-29
[FONT=Courier New][FONT=Arial][COLOR=DarkOrange][B]i have a list of names in format
second-name, first-name
and i wrote regexp to interchange it and remove the commas
i have written regexp to determine any sequence of small characters and abbreviated names like M. J. and A. K. etc
here only abbreviated names got interchanged and not the others[/B][/COLOR][/FONT]

pankaj@ubuntu:~/linux$ sed 's/\([a-z]*\), \([a-z]*\)\([A-Z. ]\{1,5\}\)/\2 \3 \1/' emp.lst 


2233| A. K. shukla        |general manager    |sales        |9000
1006|singhvi, chanchal        |director        |sales        |9500
1245| S. N. dasgupta        |manager        |sales        |7600
1114|aggrawal, anil        |manager        |sales        |8500
5684|chakrobarty, sumit        |deputy general manager    |marketing    |7000
5541|chowdury, lalit        |director        |marketing    |8000
6612| J. B. saxena        |general manager    |marketing    |6140
2358| V. K. agrawal        |genaral manager    |marketing    |8900
5601|sharma, jai        |director        |production    |5900
4478|sengupta, barun        |director        |personnel    |6800

[COLOR=DarkOrange]**[FONT=Arial]thnx in advance[/FONT]**[/COLOR][/FONT]

---

### Post by akelsall on 2009-10-30
Hello pankajphartiyal,

    Can you give us a sample of what you want the final output to look like? Also, will all the names in the list have just initials for the first part of their name (as shown), or could it vary?

Thanks,

Andy

---

