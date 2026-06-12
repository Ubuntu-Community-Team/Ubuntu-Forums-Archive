---
title: "Best tool to view memory leak..."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by obscur156 on 2010-04-30
Hi guys,i want to know what is the best tool to check for a memory leak.

Of course i have that memory leak bug and it really disapoint me...
Never had that with karmic and with a clean install of Lucid 64 bit after 24 hours it hits me for the first time just like the beta's.

i managed to check with system monitor and htop but i dont see anything consuming too much memory like 12% of 4 gigs of memory.

Is there any other way to check for memory leak or a different tools or logs than i can check.Three years and a half using ubuntu and never had that problem.This is a huge regression.

A very disapointed Lucid user...

Thanks ,best regards.

---

### Post by P4man on 2010-04-30
> **obscur156 said:**
> 
Of course i have that memory leak bug a

...

i managed to check with system monitor and htop but i dont see anything consuming too much memory like 12% of 4 gigs of memory..

So how did you come to the conclusion you had "that" memory leak bug (which was patched before the release) ?

---

### Post by obscur156 on 2010-04-30
My pc went to a crawl but i had the time to check with system monitor and htop but i could not see anything wrong.

My mouse was moving sooo slow thath it took me like 5 minutes to check.

Thanks for trying to help. Best regards.

---

### Post by P4man on 2010-04-30
a  memory leak would show up in htop (or system monitor if you set it to show ALL processes, and not just yours) by constant increase amount of memory usage for a certain process.  last time I had a xorg memory leak it would use upwards of a gigabyte in a matter of hours and would not stop until I ran out of all my physical and virtual memory. That was a pretty big leak :)

If you dont have abnormal memory usage, it seems you are facing another problem.  IS your system fully up to date?

---

### Post by obscur156 on 2010-04-30
Yes my system is fully up to date.It happened to me with the beta's and now with the final release stable.

Never had that with Karmic,its very weird,Cant put my finger on it.

---

### Post by obscur156 on 2010-05-03
Did not find what was causing the freezing but i have install the last kernel RC6 and no more freezing.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/")

Hope this helps all the people having their pc freazing.

Best regards and have a nice day.

---

### Post by obscur156 on 2010-05-03
This is so untrue...
Pc just freeze a couple of minutes ago while using opera beta.

I was not able to click on system monitor or anything else to check for memory leak.The mouse was very slooooowwwwww but the pc was not responding when clicking on anything.

This is getting very annoying + the slow transition between login screen and the desktop...Huge regression again.This is bad news for me...

Worst version ever for me in 3 years and a half on ubuntu.Thats just me.

Best regards

---

### Post by P4man on 2010-05-03
does switching to a terminal (control+alt+f1) work? Cant you find anything in the logs that give a clue?

---

### Post by obscur156 on 2010-05-03
Did not think of switching to terminal,but will try to think the next time it will happen.

If you can give me the location of the logs,i will investigate that.

Thanks for your help and time P4man.

Off to work now so i will not be here for 12 hours or more.

Thanks again ,best regards.

---

### Post by P4man on 2010-05-03
Youve been using ubuntu for 3.5 years and never needed to check your logs ? 

Anyway, they are in /var/log. Easy way to view them is system > admin > log file viewer. Many logs have time stamps, use that to find events that occurred during the freezing (so take note of the time when it happens).

---

### Post by obscur156 on 2010-05-04
Yes,you read that right,never had to check my logs in 3.5 years.
Gees never saw the log viewer in system admin lol.

I will check that when i wake up at noon.

Thanks for your help.
Best regards.

---

### Post by obscur156 on 2010-05-04
Wow there is a bunch of logs there.
Do you know where it would be the best place to check to find logs about my freezing problem?
Like Xorg.o.log,debug,kern.log,messages,syslog?

Will take me forever to check all of those :(.

Off to work again,best regards and thanks.

---

### Post by P4man on 2010-05-04
syslog and messages I think, but tbh its not entirely clear to me either what kind of messages go where and there is a clear overlap.

Either way, its not difficult to find if you search by time. Like I said, if it ever freezes again, look at your clock. Then look for events at that time.

---

### Post by obscur156 on 2010-05-05
I will check that when i get up.Now going to bed.

Thanks for your precious time and info,i appreciate it very much.

Regards,have a nice day.

---

### Post by obscur156 on 2010-05-16
Well its sad but i have wiped Lethal Lynx from my hard drive and put back Karmic and running fine.

I have Lucid running fine on my laptop,the only difference between the laptop and desktop is the nvidia graphic card on the desktop sort of...

So probably nvidia driver messing up my pc,hardware compatibility problem.
Who knows.

Thanks for your help P4man,best regards.

---

### Post by obscur156 on 2010-06-01
I finally found my problem,
I had a slowly dying memory stick...

Did a memtest86+ and found that one of the two installed was bad.
Kingston brand died after two years and a half.First time for me in 12 years of computing.

Next time i will probably buy something else...maybe with heatsink too.

So back to Lucid and i apologize for the Lethal thing little Lynx.#-o

Best regards.

---

