---
title: "Log Maintenance question"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by held7over on 2010-10-27
I notice that the logs at /var/log/ sometimes have groups of logs, for example, 

kern.log
kern.log.1

Let's say something is going wrong and tons of messages are being put into kern.log and it has grown to 500 MB or 1 gig and I want to shrink it. So 
I 'cd /var/log' and say 'sudo echo n- > kern.log' to erase the contents of kern.log.  

Should I also blank kern.log.1 ?

I looked for some GUI routine in UCC that might do this, but didn't find one that I recognized.

Thanks! :)

---

### Post by bioterror on 2010-10-27
> **held7over said:**
> I notice that the logs at /var/log/ sometimes have groups of logs, for example, 

kern.log
kern.log.1

Let's say something is going wrong and tons of messages are being put into kern.log and it has grown to 500 MB or 1 gig and I want to shrink it. So 
I 'cd /var/log' and say 'sudo echo n- > kern.log' to erase the contents of kern.log.  

Should I also blank kern.log.1 ?

I looked for some GUI routine in UCC that might do this, but didn't find one that I recognized.

Thanks! :)

And the answer to your problem is: [http://linuxcommand.org/man_pages/logrotate8.html]("http://linuxcommand.org/man_pages/logrotate8.html")

To be more accurate:

sudo nano /etc/logrotate.conf

remove # mark from the line saying "#compress"

And now it will compress your logs and you can use zcat or something to view compressed log files.

---

### Post by held7over on 2010-10-27
Thanks bioterror!  I made a note on that, as it looks to be useful, but it isn't exactly what I needed to know. I mean, compressing the files would be fine I guess, but if something is racing out of control, that isn't going to be the solution. Are these logs permanent recording everything from the INSTALL forward in time, or do they clean themselves up?

You see, I asked this question as precursor to another question I am going to ask on the forum in tracking down a problem. Last week my install was less than a week old, and 3 of the logs grew from being tiny to over 8 gig in size and I was rapidly running out of room in my "/" partition as in: 

Danger Will Robinson! Danger!

The alert given by the computer was my first warning and by that time  trying to view one of the three logs caused my system resources to overload rendering me unable to execute any further commands, and after a while of waiting I calculated that the few hundred megabytes I had left were going to be filled before my viewer showed me squat. So, not knowing what happens when a partition gets totally full and we hit the END OF FILE type thing, I paniced and shoved my install disc into the drive and rebooted and did a new install of "/"......then remembered I could have used the liveCD to view the logs and report the problem. :(

Since my new install, I have been monitoring the three logs for the last four days since, and for three days they were measured in kilobytes which made me think maybe I had wiped the problem out with the install, but yesterday they jumped to 250 mb and I got to thinking maybe I should have some way to clean those files out in case I need to jump in and control the growth rate when it really gets going. I was about to erase the contents of those files with my finger over the ENTER key, when I thought, hmmmmm, what about their program relationship with the secondary sub files??? And so, I asked this question of whether or not I should erase those also or if doing any of this was going to mess up my system?

I just checked again and discovered those three files have now shrank all on their own back to 196 mb. So, I am still watching, although I have some 
things I could report on the forum....but the extreme rate of growth that I experienced before doesn't seem to be happening yet.

---

### Post by SeijiSensei on 2010-10-27
By default logrotate keeps four previous weeks of backup logs numbered .1 through .4 respectively.  It's controlled by the "rotate" parameter in /etc/logrotate.conf and in the service-specific configurations in /etc/logrotate.d/.

---

### Post by held7over on 2010-10-28
Thanks. I will try using logrotate.

---

### Post by JKyleOKC on 2010-10-28
You can also manually delete the .2, .3, and .4 copies of the files if you don't want to keep them around for troubleshooting. Basically, each time that logrotate rotates a log file, it first deletes the highest-numbered archival copy, then renames each of the others to have the next higher number at the end of its name. This leaves no .1 copy, so that it can rename the current log as .1, and then create a new empty log file.

I've noticed that since I installed Lucid, the pulseaudio process writes a huge number of entries to several of my log files. They haven't gotten anywhere near the size that you report, but have easily doubled the size of the files as compared to similar files in my previous Hardy installations.

In your situation, I would get rid of the older archival copies of all the logs, keeping only the .1 archives, then set logrotate to compress when archiving. This should free up enough space to buy you time to study the logs and determine what's causing them to grow so rapidly.

---

### Post by held7over on 2010-10-28
Thank JKyleOKC !!!  

That is exactly what I needed to know! I was afraid of messing my system up by delete or blanking files without knowing how the files were inter-related. I will do it just as you suggest.

---

