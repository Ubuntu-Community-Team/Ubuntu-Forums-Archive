---
title: "lookingfor .wine/windows/system folder - cannot find"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by carusoswi on 2011-02-06
Running 10.10 Desktop, lookingn for the subject folder because I need to copy into it some .dll files in order to get a piece of software to run (Sony's IDS software for my digital camera).

I read that this folder is located in the HOME directory, that it is hidden.  If I go to HOME, set to 'show hidden files', not a single additional file appears.

What am I doing wrong?

Thanks in advance for any replies.

Caruso

---

### Post by Paqman on 2011-02-06
Hit control-L, and tell us the full path of the folder you're looking in. You should be in /home/yourusername.

You can also hit ctrl-H to toggle hidden files on and off. You should get loads of them show up if you're in the right folder, one of which will be .wine.

---

### Post by carusoswi on 2011-02-06
Thanks for the response.  What I read told me to load the necessary files in /home, not /home/'username', and, perhaps I should have known that I needed to look in 'username', but I did not.  Thanks for the heads up.

However, I should note that, while poking around ignorantly, I did have a close look in that /home/'username' location, and, while there were many an .xxxx file, there was no reference to .wine.

I think the problem had to do with the fact that, while I had installed Wine on my system, I did so to install this specific bit of software, and had not actually installed the subject software or any other software using Wine on this system.

I decided to install my subject softare without the dll files, and believe I noticed Wine configuring (probably creating) that .wine directory in the process.  An even more pleasant surprise welcomed me in that the software installation process completed smoothly, and it runs under Wine perfectly with no further .dll copying on my part.

Looking back at the source of my instructions, I see that they are from 2008, so, perhaps outdated for the current version of Ubuntu and/or Wine (I installed the beta version of wine found in the Ubuntu repository).

I also own Crossover, but my version is a few years old, and, it is my understanding that whatever version of Crossover one runs it's Wine implementation is probably a version or two older than the currently available non-Crossover version.

When I tried to install this software using Crossover, the install would hang after I hit 'Finish' to complete the process.  A reboot was my only escape when this happened, and, further, when I rebooted, my desktop had a minor bug in that the logout/shut down menu had been pushed off the top right of my screen and was inaccessible to my pointer.

Total uninstallation of Crossover restored the Desktop to its former state.

In any event, my IDS software appears to function perfectly (one less reason to use Windows) except that I cannot register Gimp as an output source.  I have to save the IDC processed file, then right-click on the resultant image file to invoke Gimp for further editing of the file - not as big a problem as rebooting into Windows to do my photo processing there.

Sorry for the longish post, but thank you for your reply.

Caruso

---

