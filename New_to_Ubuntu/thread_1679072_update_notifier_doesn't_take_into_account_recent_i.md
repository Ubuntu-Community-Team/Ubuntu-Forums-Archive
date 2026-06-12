---
title: "update notifier doesn't take into account recent installed updates."
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Edric Technology on 2011-01-31
Hello, friends, as you've read, I have a litlle problem. Until now it hasn't brought any problems to my software, but I think it might bring harassment and problems in the future (not to mention that it bothers me a lot):

    - My update notifier icon appears all the time in the notification area, even when I had just updated my system. And additionally, the Update Manager, after updating, seems don't taking into account the recently installed software. That is, after updating, instead of showing the message "The package information was last updated less than one hour ago", it just ignores the updating (yet it had actually installed the updates) and shows the same message as before(today, for instance, it shows "The package information was last updated 13 day ago". Yesterday, it was "12 days ago", tomorrow, it will be "14 days ago" and so on. During all these days I have updated my system without problems, but this keep appearing without any reason. This problem occurs no matter whether I selected 'ubuntu netbook remix' or 'ubuntu desktop edition' when logging up.

I've taken a look at the settings but I'm sure they're all unchanged. Anyway, the settings don't include changes that can affect this kind of behaviour, so it's odd.

Thanks in advance (I'm from Brazil, so take this into account when considering my English, please).

---

### Post by cariboo on 2011-01-31
Have you tried updating the package list manually?

You can do it two ways, go to System->Administration->Synaptic Package Manager, and click the reload  button, then click the status button in the lower left, this will show you what packages are available for update, or you can do it in a terminal, by typing:

```
sudo apt-get update
```

once the update has finished, check update-manager to see what it says.

---

### Post by Edric Technology on 2011-02-03
cariboo907, first of all I'd like to thank you. However, I tried the steps you've suggested (the two ways), but I've got error messages. Maybe they can help us to figure out what's happening.

I sent three screenshots of the errors I've got, the error.png and error2.png are screenshots of the errors I've got trying the first way you've suggested (because the error messages scrolled off the window I had to send two screenshots) and the last one (error3.png) is a screenshot of the terminal, when I was trying the second way.

It seems to me that the problem is related to public keys signature. I know a bit about public keys, and I think I know how to get one, so if this is the problem, please, tell me.

Today I updated my system the old way (using the Update Manager). I had 158 MB of software installed and the Update Manager seems to ignore it completely. Now it says "The package information was last updated 16 days ago.". It's sad.

Thanks again, and please, help me!

---

### Post by mcduck on 2011-02-03
You need to install the missing signing key. And make sure the Opera repository is actually working.

The Update Manager isn't able to access all configured repositories, so it's not able to do a proper update. Which is also why the counter for last update time doesn't reset.

---

### Post by Edric Technology on 2011-03-10
Many thanks to all of you! I've solved the problem. It was the Opera repository which have caused all the problem. I've removed the software from the netbook and the repository address in the settings menu in update manager. Thanks to all of you and mcduck (which have first pointed to the problem with the opera repository), I've solved the problem.

Forgive me please for I'm so busy that I couldn't make it faster, so it took several weeks. Thank you for the patience.

Now my system is really up-to-date.
:popcorn:

---

### Post by minj on 2011-07-25
I have the same problem. However all updates work fine. I even disabled all third-party software and ran package information update again to no avail. 

My update time counter is stuck.

---

