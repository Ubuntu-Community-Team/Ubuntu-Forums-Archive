---
title: "I need software to supervise my internet bandwith"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by xinloiemnham2 on 2008-08-08
Sorry about my English, it's so bad.
As I 've written on the title, can someone show me a software to supervise my internet bandwith.
I want to know how much I 've downloaded and uploaded while surfing the network and do anything through internet.
I've search on google and find out ntop, I 've installed it, but I can't run it, in terminal:
> Sat Aug  9 07:36:42 2008  NOTE: Interface merge enabled by default
Sat Aug  9 07:36:42 2008  Initializing gdbm databases
Sat Aug  9 07:36:42 2008  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: File open error
Sat Aug  9 07:36:42 2008  Possible solution: please use '-P <directory>'
Sat Aug  9 07:36:42 2008  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Sat Aug  9 07:36:42 2008  CLEANUP[t3055118784]: ntop caught signal 2
Sat Aug  9 07:36:42 2008  THREADMGMT[t3055118784]: ntop RUNSTATE: SHUTDOWN(7)
Sat Aug  9 07:36:42 2008  CLEANUP[t3055118784] catching thread is MAIN
Sat Aug  9 07:36:42 2008  CLEANUP: Running threads
Sat Aug  9 07:36:42 2008  CLEANUP: Locking purge mutex (may block for a little while)
Sat Aug  9 07:36:42 2008  CLEANUP: Locked purge mutex, continuing shutdown
Sat Aug  9 07:36:42 2008  CLEANUP: Continues
Sat Aug  9 07:36:42 2008  PLUGIN_TERM: Unloading plugins (if any)
Sat Aug  9 07:36:42 2008  CLEANUP: Clean up complete
Sat Aug  9 07:36:42 2008  THREADMGMT[t3055118784]: ntop RUNSTATE: TERM(8 )
Sat Aug  9 07:36:42 2008  ===================================
Sat Aug  9 07:36:42 2008          ntop is shutdown...        
Sat Aug  9 07:36:42 2008  ===================================

Please help me. Thanks.

---

### Post by ad_267 on 2008-08-08
vnstat works well. It's command line only though.

```
sudo apt-get install vnstat
sudo vnstat -u -i eth0
man vnstat
vnstat
```

---

### Post by xinloiemnham2 on 2008-08-09
Thank you, I'll try it.

---

### Post by ad_267 on 2008-08-09
I should mention that this line sets up vnstat and assumes that your internet is on eth0
```
sudo vnstat -u -i eth0
```
You might have to change it to suit you if you have wireless or dial up.

---

### Post by xinloiemnham2 on 2008-08-09
thanks, I typed :
> sudo vnstat -u -i eth1
but error:
> Error:
Unable to read database "/var/lib/vnstat/eth1".
-> A new database has been created.

then what I do now, this program is not GUI so it's difficult for newbie.

---

### Post by SkonesMickLoud on 2008-08-21
> **xinloiemnham2 said:**
> thanks, I typed :

but error:

then what I do now, this program is not GUI so it's difficult for newbie.

Sorry that this question's been sitting here for a week.

The "error" you saw is normal.  It's simply a cryptic way of saying "I see you've never run me before, I'll set up a log file for you."  It's not an error at all.

IMO the best way to check the output of vnstat is to use Conky.  You can see how to set up Conky with these threads:

[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky)
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

And how to add the output of vnstat to your Conky here:

[http://ubuntuforums.org/showthread.php?t=837658&highlight=vnstat&page=2](http://ubuntuforums.org/showthread.php?t=837658&highlight=vnstat&page=2)

If you don't want to set up Conky, just type:

```
vnstat
```

Into a terminal.

---

### Post by ad_267 on 2008-08-21
Sorry I didn't see you had edited your post to ask for help. Yes you can use conky if you want which is what I do. You can also go to applications - accessories - terminal and then just enter "vnstat". Type "man vnstat" to get more information on how to use different options. Eg you can type "vnstat -d" to get information for days, "vnstat -h" for hours etc.

---

### Post by dfmalh on 2009-04-10
Hi, I am new to vnstat, and I have a few questions.

[LIST]What is the "cron job"? ...is this the file that is created at the setup of vnstat that stores all the information, e.g. the amout of data send and received?[/LIST]

[LIST]Do I have to run "vnstat -u -i eth0/eth1 everytime I start the PC? If so, is it fine to add it to my "Sessions" that load on startup?[/LIST]

I would like to include the information in my desktop conky... can you please explain the commands below, or correct me where I am wrong?

```

Down: ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'} 
Up: ${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}

```

[LIST]execi: create a task executing the function "vnstat"[/LIST]
[LIST]300: a time interval? every 300 sec?[/LIST]
[LIST]...now the command is piped to find "today" ,and[/LIST]
[LIST]...again piped to give/print the output of $2 and $3 (e.g. in top line of the code)[/LIST]
[LIST]This will give the amount of data downloaded today[/LIST]


*In my outpu, where/which is $2, $3, $5 and $6?*

Here is an example of my output when I run "vnstat"
```
laptop:~$ vnstat

                     rx      /     tx      /    total    /  estimated
 eth1:
         today    510.44 MB  /   82.93 MB  /  593.38 MB  /     896 MB

 eth0: Not enough data available yet.

```

...and here is an example of my output when I run "vnstat -i eth1 -d
"
```

 eth1  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   10.04.    510.44 MB  |   82.93 MB  |  593.38 MB   %%%%%%%%%%%%%%%%%%%%%%:::
------------------------+-------------+----------------------------------------
 estimated      771 MB  |     124 MB  |     895 MB

```


Thanks for your help.

---

### Post by dfmalh on 2009-04-10
Hi again,

I was also wondering if I want to display the downloads for e.g. eth1, do I change my code from:

```

Down: ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'

```

to 

```

Down: ${execi 300 vnstat -i eth1 -d | grep "today" | awk '{print $2 $3}'

```


Thanks for you help.

---

### Post by dfmalh on 2009-04-10
Another stupid question....

For what does the rx and tx stand for? The total is obvious...

Thanks.

---

### Post by SkonesMickLoud on 2009-04-10
rx = recieved
tx = transmitted

---

### Post by dfmalh on 2009-04-11
Hi SkonesMickLoud,

Thanks for clearing that up for me. Maks perfect sense, I honestly don't know if I missed the explanation somewhere... I have read so many things to try and figure all this out.

Any help on my two previous two posts?

Thanks

---

### Post by ad_267 on 2009-04-11
See [cron]("http://en.wikipedia.org/wiki/Cron") for an explanation of what it does.

> Do I have to run "vnstat -u -i eth0/eth1 everytime I start the PC? If so, is it fine to add it to my "Sessions" that load on startup?
No. That just sets everything up initially. The -u option means update. vnstat will run automatically.

> Down: ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'} 
Up: ${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}

    * execi: create a task executing the function "vnstat"

    * 300: a time interval? every 300 sec?

    * ...now the command is piped to find "today" ,and

    * ...again piped to give/print the output of $2 and $3 (e.g. in top line of the code)

    * This will give the amount of data downloaded today


execi means EXECute at a set time Interval. Piping to grep finds the line with the word "today" in it. Awk prints the second and third word in the line (words are separated by whitespace). In this case the second word will be "510.44" and the third will be "MB". Have a a look [here]("http://www.ibm.com/developerworks/library/l-awk1.html") for more info on awk.

> I was also wondering if I want to display the downloads for e.g. eth1, do I change my code from:

Down: ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'

to

Down: ${execi 300 vnstat -i eth1 -d | grep "today" | awk '{print $2 $3}'


Have a look at "man vnstat" and try the different options, the -i option selects the interface and -d shows totals from previous days, so you want to use the -i options but not the -d option.

---

### Post by dfmalh on 2009-04-12
Hi thers, and thank to **ad_267** for all the information.. I played around with it and and this is what works for me at the moment...

...here is the code for day/week/month...

```
WLAN Summary${hr 1}
Downloads${goto 150}${color1}Uploads
#${color1}Today:$color${goto 60}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $2 $3}'}${goto 150}${color1}Today:$color${goto 210}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $5 $6}'}  
#${color1}Week:$color${goto 60}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $3 $4}'}${goto 150}${color1}Week:$color${goto 210}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $6 $7}'} 
#${color1}Month:$color${goto 60}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150}${color1}Month:$color${goto 210}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
```

...this will show the downloaded and uploded date in MB/GB... 

Take note that the "-d" command does not work if you want the *days* amount of data to be shown, just spesify the device.

I am not happy with the total amounts displayed, it seems very high... also this eth1 is my WiFi device, so maybe, the high amount of data can be explained by the comunication between my laptop and the router??? I don't know yet....

---

