---
title: "unable to add attachments IN ANY mail (not just hotmail)"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by balkie99 on 2009-04-07
Hi there!

I am new to ubuntu, use I. Ibex, Firefox.
I use hotmail, gmail and a university mail system (runs sun java messenger) and I can not upload any attachments to any of these.
I click "attach" and a window comes out, where I could choose from files in an ideal case, but this is inactive, I cannot choose anything, nothing opens.
Help would be appreciated!
I tried the well-known user switching i firefox, but it does not work (and even if it would, for gmail it should be no problem).
Tried to configure Evolution for hotmail, but it cannot be accessed (it says I should pay for accessing...) and there are my two other accounts.
Is this a problem with Firefox or with Ibex?
Thanks.

---

### Post by CLomax on 2009-04-07
Either Java isn't installed, in which case you should run...
```
sudo apt-get install ubuntu-restricted-extras
```
...in the terminal.

Or, failing that, you could be running the NoScript extention for Firefox which is blocking the java from running. Right click on the troubling page, go down to NoScript submenu and allow the website to run scripts.

:KS

---

### Post by balkie99 on 2009-04-07
Thank You,

I have installed Java right after switching to Ubuntu.

I cannot find the No Script in menu in Firefox, but I tried in Opera, there I could find enabling scrips, but again, nothing helps. It stops at the "open file" window and I cannot select any files.
Because it happens in Opera as well, I think it might be a wider problem of my system.
Heeeelp! Thanks for all those who are at least trying...

oh, and: I have checked my addons is firefox-I do not have NoScript, and my Java is 1.6.update 10. I know that there is an update 13 but this should not be the problem

---

### Post by balkie99 on 2009-04-09
A solution, but what is this???

Check this out.
What I did today, was to download the latest updates for Ibex.

Then, just to see, I tried attaching files- and it works, BUT somehow strangely:

Lets say I have a folder Documents, and in it a folder ABC, and it that some files, from which I would like to upload.

I click the Browse button in the mail window (for example my work mail). A windiw opens: Open file. Now, I can click on the left to Documents. On the right, my folders appear, including ABC. BUT! If i click on ABC, nothing happens, even the active "orange" line does not skip to it from the first row.

but If after clicking Browse, it opens Open file window, and THEN i click to maximize this window, I click on folder ABC and it opens and I can choose my file.

AND! If I do not maximize the Open file window, and click on ABC, it does not show any activity, but after this maximizing - it shows files in ABC. 

I can not understand it, maybe some programmers might, but I tried it several times and it works this way. 
Let me know, if you find out why, now I am happy that it works. (but it would be useful to know why, so next time i could deal with it better...)

---

### Post by cariboo on 2009-04-09
It seems to me that you have a file manager problem. I would suggest you go to System-->Administration-->Synaptic Packae Manager and search for nautilus, once synaptic has found it, rick-click it and mark it for reinstallation.

Jim

---

### Post by balkie99 on 2009-04-09
Hi Jim!

At last, an expert. BUT check this!
It had worked as I described, but I wanted to make it the way you described. I reinstalled those nautilus components, which had been installed (I do not know if I had done it right, but marked them as to reinstall and apply). And when I tried to attach files, the comp freezes! I repeated reinstalling nautilus but it freezes while trying to attach again and again. Now what...?
Thanks for your time!

---

### Post by balkie99 on 2009-04-11
I got a hint that it might be nautilus problem...So I did, what i had been said and reinstalled nautilus...the things started to NOT work again.

Since then I have reinstalled the wholu ibex, but have the same problem. 
Now, my comp freeze every time I click upload or attach and browse in any website. 

A changed nautilus to thunar, but nothing happened, freezing.
I have installed the Gnome Do, but think that does not do anything.

What to do? There must be a command or test I could run to see where is the problem, not?

---

### Post by balkie99 on 2009-04-13
Last?

Hi, so....I have reinstalled to 64bit, but the problems stayed here.

 A difference: when I click visaul effects to normal or extra, the above things happen. When leaving it on "none", so no fancy visual effects, then everything works. I do not know, what the cause is, but surely will not change this...
As anyone gets an idea, what had caused my problems, please, let me know.
Thanks.

---

