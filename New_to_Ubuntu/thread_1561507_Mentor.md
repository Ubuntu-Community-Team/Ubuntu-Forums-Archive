---
title: "Mentor"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by kerryh_r on 2010-08-26
Hi all

I am completely new to Ubuntu, although not Unix. I'm a Freelance programmer, host developer, currently "resting" between projects.
I am very keen to broaden my experience, improve my Linux/Unix skills, with a view to moving into that area of work.

To start I am interested in having a PC with a dual boot Linux/Windows option, although I have an option to use a machine as a stand alone dedicated Unix machine.

Initially I'd simply want to perform the same type of tasks I currently perform on a Windows machine, email, chat, web browsing, office type tools, bit torrent, etc, but ultimately like to move into more technical areas, like wireless security. Obviously this will entail brushing up my pretty rusty shell commands, and what I'm looking for is someone that would be prepared to offer me their services as a mentor, maybe once or twice a week, via email or chat, when I have queries, or need advice. Maybe more frequently if we get along.
As I say, I come from a professional background, I can maybe offer something in return in terms of my analysis, programming, and DB skills.
Basically looking for someone similar, patient, that has a bit of time on their hands, that might enjoy mentoring a fellow pro over the initial stages, and maybe beyond.
I'm a UK native, based in Zurich Switzerland. Of course the nearer the better, as there would always be the opportunity to chew some fat over a beer or three.

Thanks for your time in reading this, and I look forward to some productive learning with some fellow pros, and enthusiasts.

Kerry

---

### Post by papibe on 2010-08-26
The idea of having a Mentor sounds so cool...

Without discouraging the pursuing of such an ultimate approach to developing skills, I would suggest an alternative interpretation:

[INDENT]"We all can be your Mentor."[/INDENT]

Just approach one task at a time, search the forums for similar problems, get into an open thread or open your own, etc. That way you can have several "minds" taking a look at your concerns.

Now, regarding the task at hand. For me, dual boot is the best. Specially if you have the pressure to have something done, and don't have the time to research/learn how to do it on Ubuntu.

I would highly recommend being ultra safe:
[LIST]
[*]Backup your files (optional: create an image of your disk).
[*]Try to resize (shirk) your partition(s) in windows first, so the installation process touch as less as possible your Windows MBR block.
[*]If you are not able to resize on Windows, use either the gparted live CD, or the Ubuntu installation disk (in the last case do not install, select something like "try" Ubuntu. Then look for gparted on the menu).
[*] Test if you're able to boot normally on Windows after you resized your partition(s).
[*]Look for your Windows installation CD, and have it handy. You probably won't need it (but just in case).
[*]Now you're acted a little paranoid ;), install Ubuntu. 
[/LIST]

There are a few minor risks. In the VERY worst case, you won't be able to boot windows (but no data lost), and you'll need to repair your windows boot block. In that event, this will help you to solve the problem:

[INDENT][http://ubuntuforums.org/showthread.php?t=1492566]("http://ubuntuforums.org/showthread.php?t=1492566")
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")[/INDENT]

Have fun, come here often, and good luck.

---

### Post by Bölvaður on 2010-08-26
add my jabber account.
You can find it on my profile under contact info, but I would suggest having more than 1 person to fall back to

---

### Post by kerryh_r on 2010-08-27
> **papibe said:**
> The idea of having a Mentor sounds so cool...

Without discouraging the pursuing of such an ultimate approach to developing skills, I would suggest an alternative interpretation:

[INDENT]"We all can be your Mentor."[/INDENT]

Just approach one task at a time, search the forums for similar problems, get into an open thread or open your own, etc. That way you can have several "minds" taking a look at your concerns.

Now, regarding the task at hand. For me, dual boot is the best. Specially if you have the pressure to have something done, and don't have the time to research/learn how to do it on Ubuntu.

I would highly recommend being ultra safe:
[LIST]
[*]Backup your files (optional: create an image of your disk).
[*]Try to resize (shirk) your partition(s) in windows first, so the installation process touch as less as possible your Windows MBR block.
[*]If you are not able to resize on Windows, use either the gparted live CD, or the Ubuntu installation disk (in the last case do not install, select something like "try" Ubuntu. Then look for gparted on the menu).
[*] Test if you're able to boot normally on Windows after you resized your partition(s).
[*]Look for your Windows installation CD, and have it handy. You probably won't need it (but just in case).
[*]Now you're acted a little paranoid ;), install Ubuntu. 
[/LIST]

There are a few minor risks. In the VERY worst case, you won't be able to boot windows (but no data lost), and you'll need to repair your windows boot block. In that event, this will help you to solve the problem:

[INDENT][http://ubuntuforums.org/showthread.php?t=1492566]("http://ubuntuforums.org/showthread.php?t=1492566")
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")[/INDENT]

Have fun, come here often, and good luck.

Hi Papibe, and thanks for the response

That sounds good for general questions, but on some occasions, I might need more of a talk through.
For instance, your response has generated several questions, but I'm not sure if our fellow members are interested in the nitty gritty. Correct me if I am wrong guys.

Why do you consider dual boot the best option?
I see the reasoning in having partitions, but what size? This machine I plan to do it on has 2 x 150GB drives. C has 70 GB free, the other, 130.
What would cause your worst case scenario, and is it a frequent occurrence after installing Ubuntu? Can it be avoided?

For sure I will be checking out the forum regularly, for tips, tricks, and software, and ultimately, offering the benefit of my experience.

---

### Post by kerryh_r on 2010-08-27
> **Bölvaður said:**
> add my jabber account.
You can find it on my profile under contact info, but I would suggest having more than 1 person to fall back to

Thanks Bölvaður. I sent you a PM

---

### Post by mastablasta on 2010-08-27
I have abour 30 GB at the moment. it's quite enough (data is mostly stored on another dfisk though). I am also running one on 20 GB disk. also plenty of space still left... Linux doesn't grow so much as windows in size.
 
Dual boot is good so you can keep windows if you need them. besides if you mess up something in ubuntu or totally mess it up and then you quickly need to do some work, you always have windows to go back to. if you have a free maschine then you might as well go full Ubuntu.
 
Also there are very good IRC channels for ubuntu support. if you need a faster solution. just start up xchat after install and it will connect you to one.

---

### Post by no2498 on 2010-08-27
is there not a whole list of mentor's on the bottom of the main page

look for some thats in your town/state

---

### Post by papibe on 2010-08-27
> but I'm not sure if our fellow members are interested in the nitty gritty.
Well, may be because the subject and your initial post put emphasis on a different direction (mentoring). Right now it's going to be more difficult to bring attention to these details. If you want more heads here right now, it would be better to start a new thread just focus on  partition suggestions and how to do that.

> Why do you consider dual boot the best option?
In my case I just have one machine: my desktop. A few days after installing Ubuntu, my sister wanted me urgently do a video conference. I tried to do it on Ubuntu, but at the moment I didn't find a solution quickly enough. So, I just rebooted my desktop to Windows and use MS Messenger (what she has BTW).

Just change that family example for a work related one, and there you have it. I am more resourceful having 2 OS. Had I have more PCs around, the history would be different.

>  2 x 150GB drives. C has 70 GB free, the other, 130.
I recommend to check this video to see if it answers your question:
[INDENT][Ubuntu Partitioning]("http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning")[/INDENT]

> What would cause your worst case scenario, and is it a frequent occurrence after installing Ubuntu? Can it be avoided?
There was a bug on the previous release of Ubuntu (10.4). That's probably making be very cautious about the installation process. I'm pretty sure it's more safe right now, if you use the current version (10.4.1).

Regards.

---

### Post by fatality_uk on 2010-08-27
While the idea of a mentor is good, perhaps asking the right questions here on the Ubuntu forums will get you a response from a much wider range of people with a great deal of knowledge. Trust me, no matter how "tough" the question, there will be people here who will give great answers. Secondly, Ubuntu is about people:

> Ubuntu, pronounced /ùbúntú/ (oo-BOON-too), is an ethic or humanist philosophy focusing on people's allegiances and relations with each other
[http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29](http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29)

So by asking questions here, you not only get your problem/question solved, but also you can add to the sum total of knowledge about Ubuntu by sharing & involving others in the process.

---

### Post by kerryh_r on 2010-08-28
> **no2498 said:**
> is there not a whole list of mentor's on the bottom of the main page

look for some thats in your town/state

Cant't see it. can you post a link?

---

### Post by no2498 on 2010-08-29
odd i was looking in it a week or 2 to ago now i dont see it sorry

---

