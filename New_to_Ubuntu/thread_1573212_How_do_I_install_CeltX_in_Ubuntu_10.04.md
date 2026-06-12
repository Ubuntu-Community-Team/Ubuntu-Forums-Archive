---
title: "How do I install CeltX in Ubuntu 10.04?"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by bronner on 2010-09-12
Hello, I downloaded CeltX for Linux off of their website, and now I have no idea how to install it. I tried extracting the files and clicking the 'celtx-bin' file, but to no avail. Can someone tell me what to do and how to install CeltX in Ubuntu 10.04?

---

### Post by qamelian on 2010-09-12
It doesn't need to be installed. You can just extract the file you downloaded to you home folder. It will extract to a folder called celtx. Inside that folder there is a script called celtx that runs to application. If it needs to be accessible to multiple user on your computer, you can extract it to /opt and create an entry in your menu to run it.

---

### Post by bronner on 2010-09-12
Well, I've extracted the files before, and it didn't work.

But now when I try to extract them to the home folder, it gives me this:

"You don't have the right permissions to extract archives in the folder "file:///home""

---

### Post by qamelian on 2010-09-14
By home folder, I mean the folder named /home/whatever_your_username_is. You should have now issue writing to that folder. 

When you extracted it before and it didn't work, what exactly happened? All I've ever done is to extract the celtx folder from the archive to my /opt folder and create a launcher in the menu pointing to /opt/celtx/celtx, and the application has run without any issues. If it still fails to work, open a terminal, and navigate to the folder containing the application. Launch it from the terminal and reply with any feedback from the terminal. That will help diagnose the problem.

---

