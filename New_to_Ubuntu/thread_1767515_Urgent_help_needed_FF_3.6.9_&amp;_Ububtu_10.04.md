---
title: "Urgent help needed FF 3.6.9 &amp; Ububtu 10.04"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by Jenferd on 2011-05-25
Help! 

Flash has just bugged out on us big time! my eldest was streaming something and it suddenly started crashing so she threw the laptop at me!!! I uninstalled it and reinstalled, then tried uninstalling both, restart then reinstalled FF, but Flash still won't work!

I've checked update manager and that's all up to date... Flash is showing as installed in the software centre but if I type in about: plugins in FF there's no sign of it.

It is very much needed over the next few days for my other daughter who is autistic and is taking some exams at home via this computer... online learning enviroment

Any help would be much appreciated :0)

---

### Post by terrykiwi83 on 2011-05-25
> 
suddenly started crashing so she threw the laptop at me!!!

Well that can't be good for the Laptop, hopefully you caught it :D

I would suggest you install FF4 ([http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/](http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/))

Also have you installed the restricted-extras? 

Hopefully something there can help

---

### Post by ICEhockeyGOALTENDER on 2011-05-25
Yes! I had the same troubles(except the throwing). FF4 helped the problem for hopefully it would help you too.

Good luck on the tests!

---

### Post by Jenferd on 2011-05-25
> **terrykiwi83 said:**
> Well that can't be good for the Laptop, hopefully you caught it :D

I would suggest you install FF4 ([http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/](http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/))

Also have you installed the restricted-extras? 

Hopefully something there can help

It's telling me to open up the *Ubuntu Software Center*, head to *Edit > Software Sources *and click the* ‘Other Software’* tab. Press* ‘Add’* .... if I go to software centre > Edit and click on software sources its not giving me an 'other software tab :(

How do I install the restricted extras?

I'm tired and not working at my best here :/

Thanks for your help :0)

---

### Post by Jenferd on 2011-05-25
> **ICEhockeyGOALTENDER said:**
> Yes! I had the same troubles(except the throwing). FF4 helped the problem for hopefully it would help you too.

Good luck on the tests!

Thanks :0) If they didn't need it tomorrow I'd be inclined to do the same now, hopefully I can get the software centre to behave before I fall asleep on the keyboard lol :0)

---

### Post by jtarin on 2011-05-25
Have you checked Firefox add-ons to see if Flash is listed? If not have you checked in Synaptic to see if Flash is installed?

---

### Post by mikewhatever on 2011-05-25
Not sure it has something to do with the crashes, but the current version of Firefox in 10.04 is 3.6.17, which puts you no less then eight updates behind.

---

### Post by Jenferd on 2011-05-25
> **jtarin said:**
> Have you checked Firefox add-ons to see if Flash is listed? If not have you checked in Synaptic to see if Flash is installed?

Yeah Fire fox says its not installed but the software centre says its is!?

---

### Post by terrykiwi83 on 2011-05-25
It can be installed with ease by putting the below two commands into Terminal:

```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Jenferd on 2011-05-25
> **mikewhatever said:**
> Not sure it has something to do with the crashes, but the current version of Firefox in 10.04 is 3.6.17, which puts you no less then eight updates behind.

I know it's up to 4... I've uninstalled and reinstalled via the software centre and still getting that as the version via help > about, if I try going on the Adobe site it says it can't decet which version and try a manual install!? Meh!

---

### Post by jtarin on 2011-05-25
Remove Flash from the software center then:
1. In synaptic package manager, completely remove libflash-mozplugin . Make SURE you use the &#8220;completely remove&#8221; option, that gets rid of the gstreamer-ugly and couple other packages.
2. Download the latest flash plugin for Linux from [www.adobe.com](www.adobe.com).
3. Unzip it to a folder on your desktop.
4. In terminal cd to that dir and in a terminal "sudo ./flashplayer-installer" (no quotes)
5. follow the prompts, and make sure the path to your plugins is right

---

### Post by Jenferd on 2011-05-25
> **terrykiwi83 said:**
> It can be installed with ease by putting the below two commands into Terminal:

```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update && sudo apt-get upgrade

```

Thankyou **SO** much that worked a treat, flash is working better than it ever did. I don't know how much you know about autism but her taking these exams is something we never thought she'd manage; if she couldn't have used this laptop tomorrow and had to go on a PC with windows we would have been in a whole world of confusion and chaos and she would have failed from the start!

You are a :KS You have helped more than you can imagine...
Thank you again... now I need to sleep for a couple of hours zzzzz :0)

---

### Post by Jenferd on 2011-05-25
Thanks for replying and trying to help much appreciated, the code for the terminal that terrykiwi83 suggested worked :0)

---

### Post by Jenferd on 2011-05-25
Thanks to everyone for there help :D :D x

---

