---
title: "how to install a driver"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by sallam on 2010-09-26
Greetings
Ubuntu couldn't find my Canon MP250 printer driver, so I've downloaded  driver manually from Canon website. Its a rar file.
But I don't know what to do next. I've decompressed the rar file and found an EULA.txt file and 3 tar.gz files. How do I install them please?
I tried system > administration > additional drivers, but nothing happened.

btw, where is the equivalent of Windows 'devise manager' where all hardware and drivers are listed?

---

### Post by philinux on 2010-09-26
This is the package you need. Download link is at the bottom of page. Ubuntu is based on debian so always go for the deb type file.

[http://support-au.canon.com.au/contents/AU/EN/0100237401.html](http://support-au.canon.com.au/contents/AU/EN/0100237401.html)

Once downloaded right click on to "Extract here" in the directory of your choice. There is a script to run the installer which is a .sh (script file) file. See this. [http://amitech.50webs.com/installing/index.php.html#script](http://amitech.50webs.com/installing/index.php.html#script)

---

### Post by QLee on 2010-09-26
sallam, you have been advised more than once to post your questions about the beta , unreleased 10.10 in the forum appropriate to questions about 10.10. Even though you mention 10.10 in your sig, many people will not notice that. You run the risk of bad advice when you ask about an unreleased version in the forum for released versions. We want you to get the best help available.

I suggest you mention that you are using 10.10 in the body of your next question.

Do you remember that a moderator moved your question about your battery to the proper forum, you seemed to understand then.
[http://ubuntuforums.org/showthread.php?t=1581660](http://ubuntuforums.org/showthread.php?t=1581660)

---

### Post by sallam on 2010-09-27
Sorry for this again. You see, I'm just a newbie.. I'm not testing the beta version. I'm only using it to get aquanted with the OS so that when it comes out after 20 days or so, I can be prepared to use it properly. My questions are not related to ubuntu beta in particular. They are common ubunt questions.
Of course, if you find otherwise in my questions, feel free to move them. And I'll make it more visible in my sig. I hope that's OK.

---

### Post by QLee on 2010-09-27
> **sallam said:**
> Sorry for this again. You see, I'm just a newbie.. I'm not testing the beta version. I'm only using it to get aquanted with the OS so that when it comes out after 20 days or so, I can be prepared to use it properly. My questions are not related to ubuntu beta in particular. They are common ubunt questions.
Of course, if you find otherwise in my questions, feel free to move them. And I'll make it more visible in my sig. I hope that's OK.
sallam, whatever you choose to do is OK, you aren't required to take my suggestions, I offer them to try and help you. I think it's still a better idea to use a released version to get acquainted with Ubuntu (there will be fewer bugs) and from the number of your posts you are struggling a bit but you choose what you do. I don't think you're just a newbie, I don't classify people that way.

I doubt repeating your sig three times is necessary, the bold and colour make it noticible.

Best of luck!

---

### Post by philinux on 2010-09-27
sallam,

My post number 2 has the solution.

---

### Post by sallam on 2010-09-27
Thanks QLee, I'll keep just one then.
Thanks philinux, the driver that got is downloaded from Canon and its for debian and tested with ubuntu as they mention. Its the installation that puzzles me.
I didn't understand the part regarding the .sh script. I don't know where to download that srcipt? I've extracted the driver file only to find 3 more compressed files in them. Its like a maze!!
Must I use a script and terminal and type stuff? where is the device manager in ubuntu? I cannot just ask ubuntu to install a priner driver and point it to where the driver file is to extract what it needs directly from there?

Looks like a big job to install a simple driver in ubuntu..

---

### Post by Paqman on 2010-09-27
> **sallam said:**
> Its the installation that puzzles me.


Don't extract the .deb. Just double click on it.

---

### Post by Tibuda on 2010-09-27
> **Paqman said:**
> Don't extract the .deb. Just double click on it.

Maybe File-Roller is associated with .deb files in the OP system. If so, right-click the .deb file and choose "Open with Software Center".

---

### Post by sallam on 2010-09-27
what deb? its a tar file. Double clicking opens the archive. Inside the tar there are several tar.gz files, and one eula.txt file..

---

### Post by Tibuda on 2010-09-27
> **sallam said:**
> what deb? its a tar file. Double clicking opens the archive. Inside the tar there are several tar.gz files, and one eula.txt file..

In the link provided, you can download a file named scangearmp-mp250series-1.60-1-deb.tar.gz. Once you extract it, theres a "packages" subfolder with four .deb files.

---

### Post by sallam on 2010-09-27
Thanks. I've finally managed to install it.
Many thanks.

---

### Post by Tibuda on 2010-09-27
> **sallam said:**
> Thanks. I've finally managed to install it.
Many thanks.

That's good!

---

