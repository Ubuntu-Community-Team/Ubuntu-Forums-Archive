---
title: "How do I add a line to my &quot;/etc/sources.list&quot;?"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by The JESTer on 2009-07-16
I was told to add a line to my "/etc/sources.list", but do not know how.

I figure I open up the terminal type "sudo " , but what next?

---

### Post by esalnoj on 2009-07-16
"gksudo gedit filepath/filename" (where filepath is path to file, filename is sources.list, in this case).

As long as the target is a text file.

---

### Post by aysiu on 2009-07-16
Just go to System > Administration > Software Sources and click Add

---

### Post by mthalis on 2009-07-16
System -> Administrator -> Synaptic Package Manage -> Setting -> Repositories -> Third Party Software -> Add
Using that you can add website.

---

### Post by The JESTer on 2009-07-17
Thanks for the quick reply. I copied command without quotes and it opened up a new window where I copied the line but got a could not find file error. I am bit new to quite understand what to do next, but the post from aysiu solved my problem in a different way. I am trying to get my printer to work.

---

### Post by The JESTer on 2009-07-17
Thank you [mthalis]("http://ubuntuforums.org/member.php?u=365700")  for teaching me another pathway to do what I needed, now I know 2 of the 3 ways suggested to me. Again thanks to everyone for helping me so quickly.

---

### Post by aysiu on 2009-07-17
To break down the three ways a bit...

There is a text file called sources.list in the apt directory, which is inside the /etc directory.

As a shorthand, people refer to it as /etc/apt/sources.list

1. Since this is a system file, you have to edit it using *sudo* or *gksudo*. Examples: ```
gksudo gedit /etc/apt/sources.list
``` ```
sudo nano -B /etc/apt/sources.list
``` and then you can paste in whatever new repository line you want.

2. There is a graphical interface for managing this file, though, and it is the command *gksudo software-properties-gtk*. This can be accessed directly through System > Administration > Software Sources.

3. You can also access *software-properties-gtk* by going to System > Administration > Synaptic Package Manager and then clicking on Settings > Repositories. This is exactly the same as #2 but just a different way to get there.

In the end, all three methods are just ways of modifying the same text file: /etc/apt/sources.list

---

### Post by bodhi.zazen on 2009-07-17
> **esalnoj said:**
> Forget sudo.

"gedit /etc/sources.list" (without qoutes) should work.

If you get a permissions error, then try sudo in front.

gedit is the default linux command for editing text files.

Edit: What are you even trying to do that requires your sources.list be changed?

Um, no.

no, no, no. :lolflag:

1. You can not save your edits without root privileges.

2. sudo with a graphical app ? shame, shame ;)

Use gksu with graphical apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

