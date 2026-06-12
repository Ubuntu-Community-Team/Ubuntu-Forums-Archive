---
title: "avast command line"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-07-31
I want to make a script that will check my server files using avast

avast -a -c /home/lance/Documents -r=/home/lance/report/avastlog.txt

I get 
#-------------------------------------------------------------------
# Date: Sat Jul 31 19:49:46 2010
# Scanned areas:
# 	/home/lance/Documents
#
#
# Statistics:
#
# scanned files: 	1909
# scanned directories: 	90
# infected files: 	0
# total file size: 	71.2 MB
# virus database: 	100730-1 30.07.2010
# test elapsed: 	4s 950ms

but i want what i see in the command line to show in the report. How do i do that? below is a sample of the command line
/home/l/Documents/readguide04.pdf	[OK]
/home/l/Documents/smb.conf	[OK]
/home/l/Documents/wireless.txt	[OK]
/home/l/Documents/xp key.txt	[OK]
/home/l/Documents/Welcome Bishop Fernando Isern.html	[OK]
Archived /home/l/Documents/.doc/_1_CompObj	[OK]
Archived /home/l/Documents/.doc/1Table	[OK]
Archived /home/l/Documents/.doc/WordDocument	[OK]
Archived /home/l/Documents/.docyInformation	[OK]
/home/lance/Documents/NOVENA TO SAINT BERNADETTE SOUBIROUS.doc	[OK]
#
# Statistics:
#
# scanned files: 	1909
# scanned directories: 	90
# infected files: 	0
# total file size: 	71.2 MB
# virus database: 	100730-1 30.07.2010
# test elapsed: 	4s 950ms
#

---

### Post by lance bermudez on 2010-07-31
this does some of what i want so far
avast -a -c /home/lance/Documents -r=*/home/lance/report/avastlog.txt

---

### Post by DaithiF on 2010-08-01
Hi,
i have never used avast, but if you just want to capture the program output to a file, then:
```
avast -a -c /home/lance/Documents &> /home/lance/report/avastlog.txt
```

---

