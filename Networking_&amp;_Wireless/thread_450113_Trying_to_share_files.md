---
title: "Trying to share files"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by lloydlloyd on 2007-05-21
Hey, been trying to get file sharing for a little while this afternoon, but with out much luck. I right click on a folder in my home directory to share, and it comes up with the following:
[IMG]http://img.photobucket.com/albums/v479/lloydlloyd/Untitled1.jpg[/IMG]
So I click on "Install services" and it whirs away until I get the following message:
[IMG]http://img.photobucket.com/albums/v479/lloydlloyd/Untitled2.jpg[/IMG]
Now, I'm new to Linux/Ubuntu, and I'm not sure what the heck this is referring to.
Any help on how to fix these broken packages would be much appreciated.
Thanks
Elliot...

---

### Post by spin2cool on 2007-05-21
Try this:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way)

---

### Post by lloydlloyd on 2007-05-21
Thanks, but that didn't seem to explain how to repair the broken packages. I am able to share files from another computer running Ubuntu, but not from my laptop. Just wanting to be able to share photos/mp3s etc across the network, but can't seem to get that to happen.

---

### Post by pebo on 2007-05-21
Open Synaptic: go to edit->fix broken packages ;)

---

### Post by lloydlloyd on 2007-05-22
That sounds like something I need to remember, but in this case, it didn't work.
I just reinstalled ubuntu.
i'm sure there may have been an easier, less time consuming process, but I am impatient.

---

### Post by pebo on 2007-05-22
You could try this next time: ```
sudo dpkg --configure -a
```but I'm not sure it isn't the same as running the Synaptic command.

---

### Post by lloydlloyd on 2007-05-23
Cool thanks a bunch for your help :)

---

