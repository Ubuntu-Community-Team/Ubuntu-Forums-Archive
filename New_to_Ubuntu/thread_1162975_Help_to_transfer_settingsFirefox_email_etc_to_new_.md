---
title: "Help to transfer settings/Firefox email etc to new machine"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Peterfc on 2009-05-18
Hi All

I have been using a machine to get to know Ubuntu 9.04. Now i am happy i wish to transfer mainly my email in Thunderbird and bookmarks in Firefox to a new machine. 

This machine is going to be used for data storage when my new machine is up and running. It's only email and Bookmarks that are an issue. 

Thanks for reading this thread

Peter

---

### Post by lovinglinux on 2009-05-18
I don't use Thunderbird, but I use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to back and restore Firefox profiles between machines or after upgrades. Nevertheless, since you just need the bookmarks, you can export them using the built in Bookmark manager or simply copy the file *places.sqlite* and paste it in the new profile on the other computer.

---

### Post by 73ckn797 on 2009-05-18
You can simply go to /home/yourname/ . There you can copy the .mozilla & .mozilla-thunderbird folders to a memory stick or whatever. Once you have installed the new Ubuntu copy those folders into the new /home/yourname folder. Then start Firefox and/or Thunderbird and your stuff will be available.

Another method for Firefox is to copy the back-up "json" extension file from /home/frank/.mozilla/firefox/"crypticnamed".default/bookmarkbackups. The "json" files are automatic back-ups. Use the one with the latest date name. The "crypticnamed.default" is simply a set of letters and numbers similar to "vkuuxfit.default".

---

### Post by Didius Falco on 2009-05-18
If you want to transfer your settings, bookmarks, extensions and saved passwords from Firefox and your email and accounts from Thunderbird, the easiest way would be to:

1.Open Nautilus, make sure hidden files are shown (CTRL+H).

2. Navigate to your Home (/home/username) directory and scroll down until you see > .mozilla  .mozilla-thunderbird 

3. Copy and paste to a Flash drive, or whatever you are using for to sneaker-net files.

4. Reverse the process on the new PC.

I have found that it helps to run and then close both Firefox and Thunderbird so they will create those directories. When you copy & paste them into the new PC, choose to "merge" and "replace" and you should be all set.

I hope this helps...

Regards,

Didius

---

### Post by 73ckn797 on 2009-05-18
> **Didius Falco said:**
> 
I have found that it helps to run and then close both Firefox and Thunderbird so they will create those directories. When you copy & paste them into the new PC, choose to "merge" and "replace" and you should be all set.

I hope this helps...

Regards,

Didius

It is not necessary to run first then restart. Thunderbird does not create its folder until the first start-up. By simply copying the previous folder into the /home folder prior to starting T'bird, it will read the info and start-up just as if things had always been there.

---

### Post by superprash2003 on 2009-05-18
[https://addons.mozilla.org/en-US/firefox/addon/2410](https://addons.mozilla.org/en-US/firefox/addon/2410)

---

### Post by Peterfc on 2009-05-19
Thanks Guys

The xmarks did the job for my book marks now all i need to do is save all my emails. 

Thanks to you all


Peter

---

