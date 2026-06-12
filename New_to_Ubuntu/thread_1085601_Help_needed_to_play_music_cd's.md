---
title: "Help needed to play music cd's"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by old_dope on 2009-03-03
I have only just come online running Xubuntu 8.10. I have managed to locate the Update Manager and installed all available updates. But for some reason i still can't play my music cd's or listen to online radio stations. Would appreciate any help. Thanks

---

### Post by Chilli Bob on 2009-03-03
The first thing I would try is to open a terminal and run alsamixer.  Check that the volume isn't muted on anything.  (Left/right arrow keys to select slider,  up/down to adjust.)

---

### Post by old_dope on 2009-03-03
How do Bob. Have to confess that i am a complete and utter Linux novice but will try and find this alsa thingy. Good on yer cobber for the reply

---

### Post by tarps87 on 2009-03-03
It is possible you need to install some of the restricted codecs, these will be the the restricted extras package:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

To install, in a terminal type
```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by old_dope on 2009-03-03
Managed to find terminal and typed in the following:
sudo apt-get install xubuntu-restricted-extras, but i must have done something wrong because i still can't play my cd's and when i try to open the Synaptic Package Manager i am informed that, "Unable to get exclusive lock"? and that apt-get is still running?

---

### Post by tarps87 on 2009-03-03
> **old_dope said:**
> Managed to find terminal and typed in the following:
sudo apt-get install xubuntu-restricted-extras, but i must have done something wrong because i still can't play my cd's and when i try to open the Synaptic Package Manager i am informed that, "Unable to get exclusive lock"? and that apt-get is still running?

What happened after you typed "sudo apt-get install xubuntu-restricted-extras"? Did it ask you for your password?
This command should have installed the restricted package, "Unable to get exclusive lock" implies that it is still installing.

---

### Post by Chilli Bob on 2009-03-03
> **old_dope said:**
> Managed to find terminal and typed in the following:
sudo apt-get install xubuntu-restricted-extras, but i must have done something wrong because i still can't play my cd's and when i try to open the Synaptic Package Manager i am informed that, "Unable to get exclusive lock"? and that apt-get is still running?

Hmmm....try rebooting, then installing the restricted extras.  If you get the lock problem again, check out this thread.....[http://ubuntuforums.org/showthread.php?t=1045019](http://ubuntuforums.org/showthread.php?t=1045019).

---

### Post by mikechant on 2009-03-03
You shouldn't need restricted-extras to play music CDs. Does your sound work at all for anything? I believe there's a sound test during the install process - did that work? Also I think the same sound test is available from one of the menu options but I'm at work on my (compulsory) Windows machine so I can't tell you where it is.

---

### Post by old_dope on 2009-03-03
I have been trying without success despite all the help to get things right until i opened a terminal and typed:

sudo dpkg --configure -a 

I had previously been typing: sudo dpkg -configure -a

When i exited the terminal and opened Synaptic a new message appeared:

You have 1 broken package on your system
Use the 'Broken' filter to locate it

I am sorry for being such a nuisance but could someone tell me how i might get hold of this and use the 'Broken' filter please. Big thanks

---

### Post by tarps87 on 2009-03-03
> **old_dope said:**
> I have been trying without success despite all the help to get things right until i opened a terminal and typed:

sudo dpkg --configure -a 

I had previously been typing: sudo dpkg -configure -a

When i exited the terminal and opened Synaptic a new message appeared:

You have 1 broken package on your system
Use the 'Broken' filter to locate it

I am sorry for being such a nuisance but could someone tell me how i might get hold of this and use the 'Broken' filter please. Big thanks


I think it is under view filters
This should have the same effect
```
sudo apt-get install -f
```


> **mikechant said:**
> You shouldn't need restricted-extras to play music CDs. Does your sound work at all for anything? I believe there's a sound test during the install process - did that work?

That is a good point, is it a music cd or a mp3 cd?

---

### Post by old_dope on 2009-03-03
Everything back to normal now thanks goodness. Thanks for all the help

---

### Post by tarps87 on 2009-03-04
Can you play music cd's now?

---

### Post by old_dope on 2009-03-04
Howdy Tarps
I can play some sound files but still no luck with cd's and dvd's unfortunately. Could i open a terminal and try to run:

sudo apt-get install xubuntu-restricted-extras

I have been told to give VCL a try out and could you tell me what is medibuntu please.

---

### Post by tarps87 on 2009-03-04
> **old_dope said:**
> Howdy Tarps
I can play some sound files but still no luck with cd's and dvd's unfortunately. Could i open a terminal and try to run:

sudo apt-get install xubuntu-restricted-extras

I have been told to give VCL a try out and could you tell me what is medibuntu please.

You can try the command, you will need to be connected to the internet.
It should ask you for your password and then if you are sure you want to install. After that it will download and install.

I'm assuming you mean VLC, this usually plays most dvd's so you can give it a try, it is in synaptic/applications -> add remove

medibuntu is a repository/store of programs/packages that aren't included in the Ubuntu distribution, I believe most of these are now in the restricted packages. To watch films and listen to music I only have to install the restricted extras.

---

### Post by old_dope on 2009-03-04
Hey Tarps i just opened a terminal and typed:

sudo apt-get install xubuntu-restricted-extras

I made sure this time that everything had finished before i exited from the terminal and tried out a cd. It works great! Thanks for all the help

---

### Post by tarps87 on 2009-03-04
That's ok, glad I could help

---

