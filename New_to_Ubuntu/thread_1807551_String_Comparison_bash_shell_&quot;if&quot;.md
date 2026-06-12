---
title: "String Comparison bash shell &quot;if&quot;"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by chrislo2004 on 2011-07-19
Here's my bash shell script

I basically just wanted to know if the script can match today as Tuesday, it failed to. So i tested output the $Match & $Date, which both comes out the word "Tuesday". As such I also did a not equal to match, and tested... i got my message come out! How come the match is not matching? when I got both the outputs as "Tuesday"??Anyone can help? Thank you first :)

[root@anonymous ~]# if [ "$Match" == "Date" ]
> then echo 'It really is a Tuesday!'
> fi
[root@anonymous ~]#
[root@anonymous ~]# echo $Match
Tuesday
[root@anonymous ~]# echo $Date
date +%A
[root@anonymous ~]# date +%A
Tuesday
[root@anonymous ~]# if [ "$Match" != "Date" ]
> then echo 'It really is a Tuesday!'
> fi
It really is a Tuesday!
[root@anonymous ~]#

---

### Post by androssofer on 2011-07-19
> **chrislo2004 said:**
> Here's my bash shell script

I basically just wanted to know if the script can match today as Tuesday, it failed to. So i tested output the $Match & $Date, which both comes out the word "Tuesday". As such I also did a not equal to match, and tested... i got my message come out! How come the match is not matching? when I got both the outputs as "Tuesday"??Anyone can help? Thank you first :)

[root@anonymous ~]# if [ "$Match" == "Date" ]
> then echo 'It really is a Tuesday!'
> fi
[root@anonymous ~]#
[root@anonymous ~]# echo $Match
Tuesday
[root@anonymous ~]# echo $Date
date +%A
[root@anonymous ~]# date +%A
Tuesday
[root@anonymous ~]# if [ "$Match" != "Date" ]
> then echo 'It really is a Tuesday!'
> fi
It really is a Tuesday!
[root@anonymous ~]#


missing $? try:
```
if [ "$Match" == "$Date" ]
```

instead of 

```
if [ "$Match" == "Date" ]
```

---

### Post by dethorpe on 2011-07-19
You are comparing the $Match variable against the actual string "Date".
 
I think what you are want to do is compare against the output of the 'date +%A' command.
 
So try :
 
```
 
if [ "$Match" == $(date +%A) ]
 

```

---

### Post by chrislo2004 on 2011-07-19
Thanks, it works now :)

[root@anonymous ~]# Match="Wednesday"
[root@anonymous ~]# if [ "$Match" == $(date +%A) ]
> then echo 'It really is a Wednesday!'
> fi
It really is a Wednesday!
[root@anonymous ~]#


> **dethorpe said:**
> You are comparing the $Match variable against the actual string "Date".
 
I think what you are want to do is compare against the output of the 'date +%A' command.
 
So try :
 
```
 
if [ "$Match" == $(date +%A) ]
 

```

---

