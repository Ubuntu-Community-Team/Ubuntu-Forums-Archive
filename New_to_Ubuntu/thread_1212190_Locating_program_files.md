---
title: "Locating program files"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by filomena on 2009-07-13
So, being a beginner, I have installed KMyMoney and put a launcher on the desktop.  When I try to find out where the program files are the only location I get is  my desktop.  Did I really install the program to the desktop and, if so, is this a smart thing to do?:confused:

---

### Post by DaGrimReefah on 2009-07-13
Most likely you didn't install it to the desktop, and if you did, it wouldn't be a big deal. But, I bet you can find the configuration file in your /home/yourname directory. If you go to "Places">"Home Folder" and then click on "View">"Show Hidden Files", you should see a folder called .KMyMoney

---

### Post by Cypher on 2009-07-13
How did you istall the package? If through The Add-Remove or Synaptic Package Manager, you should be able to go back in these apps and highlight the kMyMoney app and have it give you details.

You can also do it from the command line with
```

dpkg -l | grep money

```
This will tell you what the name of the package is (probaby kMyMoney), then do
```

dpkg -L kMyMoney | more

```
This will show you all the files from that package and where they are located..

---

### Post by philinux on 2009-07-13
> **filomena said:**
> So, being a beginner, I have installed KMyMoney and put a launcher on the desktop.  When I try to find out where the program files are the only location I get is  my desktop.  Did I really install the program to the desktop and, if so, is this a smart thing to do?:confused:

Hi, welcome.

My guess is you downloaded from the kmymoney site. This is a package which needs compiling. you would have downloaded to your desktop I bet.

The best/easiest way to install most stuff is from add/remove, Apps>Add/Remove or synaptic. The latter is from system>admin>synaptic package manager.
Search for kmymoney and right click it to mark for installation then the apply button.

Have a look at this link. [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
And I would urge you to read the sticky threads on the forum.

---

