---
title: "Three questions? RAM, Empathy, and 7-zip"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by ChubbySauce on 2009-07-24
-Why does system monitor only recognize 3.1GBs of ram? Does this mean ubuntu is only using 3.1 gigs of ram. how do I get it to recognize and use all four gigs of ram?
here are my specs.   [http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12139188-78299199-78299212-78299212-78299212-81749852-81978909.html](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12139188-78299199-78299212-78299212-78299212-81749852-81978909.html) 


-Could someone walk me through setting up a video chat (MSN) with empathy instant messenger I can't find any video options?


-I couldn't get ubuntus default extractor program to open a rar. file so I downloaded 7-zip through synaptic package manager but 7 zip is not in my apps bar. I also redownloaded it still nothing. Could someone help me with 7-zip?

---

### Post by Finalfantasykid on 2009-07-24
You are using the 32-bit version of Ubuntu.  32 bit can only access up to 4GB, but it is always less than that since you have to also include any other devices in your hardware(Graphics cards, etc.)

For example, I have 4GB of Memory, but since I am using the 32-bit version of Ubuntu, I can only access 3.2 GB.

I don't know how to answer your other questions :(

---

### Post by oOarthurOo on 2009-07-24
No need for 7zip
```
sudo apt-get install unrar
```

---

### Post by gastly on 2009-07-24
I agree with Finalfantasykid. As for the other questions...

- Try an read this FAQ, it will answer your question about Empathy [http://live.gnome.org/Empathy/FAQ](http://live.gnome.org/Empathy/FAQ)

- As for rar support, the 7zip you downloaded is the commandline version, it does not provide a GUI (I think GUI version is not available for Linux).

You can get rar support in the default Archive Manager of Ubuntu (File Roller), by the following command:
```

sudo apt-get install p7zip-full p7zip p7zip-rar

```

---

### Post by zeroseven0183 on 2009-07-24
> **ChubbySauce said:**
> 

-I couldn't get ubuntus default extractor program to open a rar. file so I downloaded 7-zip through synaptic package manager but 7 zip is not in my apps bar. I also redownloaded it still nothing. Could someone help me with 7-zip?

It's somewhat strange that you are not able to extract files. Have you tried "Open With Archive Manager" when you right-click on a RAR file?

Here's a very helpful site you can use to "generate" commands for Terminal: [http://www.howtoadvice.com/7zipHelper/](http://www.howtoadvice.com/7zipHelper/)

That would be a good start.

---

### Post by egalvan on 2009-07-24
> **Finalfantasykid said:**
> You are using the 32-bit version of Ubuntu.  **[COLOR="Red"]32 bit can only access up to 4GB, [/COLOR]**
 it is always less than that **you have to include other devices in your hardware(Graphics cards, etc**.)

I have 4GB of Memory, but since I am using the 32-bit version of Ubuntu, I can only access 3.2 GB.
(

32-bit systems CAN access more than 4GB if PAE is enabled in hardware/software.

The SERVER version of 32-bit Hardy can access up to 64GB.
Install the server version, then install a GUI on top.
Instant access to more than 4GB RAM.\
I ran this for over a year ( now I have full 64bit hardware/software ) with 8GB RAM

And yes, other devices can eat up RAM space... so the amount available is almost always less than amount installed.

---

### Post by zeroseven0183 on 2009-07-24
> **ChubbySauce said:**
> -Could someone walk me through setting up a video chat (MSN) with empathy instant messenger I can't find any video options?

I haven't use Empathy as my IM, I usually log on using Pidgin but the two only supports text chat. I know of two other IM applications that have video chat support, **Kopete** and Skype. To use your webcam, you need to have **Cheese**.

---

### Post by frunns on 2009-07-24
> **egalvan said:**
> 32-bit systems CAN access more than 4GB if PAE is enabled in hardware/software.

The SERVER version of 32-bit Hardy can access up to 64GB.
Install the server version, then install a GUI on top.
Instant access to more than 4GB RAM.\
I ran this for over a year ( now I have full 64bit hardware/software ) with 8GB RAM

And yes, other devices can eat up RAM space... so the amount available is almost always less than amount installed.

Isn't it easier just enabling PAE? Can't remember the exact steps, but compared to a reinstall, of the server version no less, I'd recommend doing it manually if there really is need for it.

---

### Post by Sef on 2009-07-24
> I haven't use Empathy as my IM, I usually log on using Pidgin but the two only supports text chat. I know of two other IM applications that have video chat support, **Kopete** and Skype.

Also Amsn has web cam support.   Applications > Add/Remove > Show: All Available Applications > Search: Amsn > tic the amsn box > apply changes > apply > close.

---

### Post by theozzlives on 2009-07-24
> **frunns said:**
> Isn't it easier just enabling PAE? Can't remember the exact steps, but compared to a reinstall, of the server version no less, I'd recommend doing it manually if there really is need for it.

When I had my 4 GB coming in the mail, I knew I was going to have problems so I went 64 bit. Wish I knew about PAE.

---

### Post by frunns on 2009-07-24
> **theozzlives said:**
> When I had my 4 GB coming in the mail, I knew I was going to have problems so I went 64 bit. Wish I knew about PAE.

Well, technically there are other benefits from 64 bit as well, I'm just not sure that you'll notice as a normal user. And the same goes for those extra 800MB of RAM... Not sure how much difference that makes.

---

### Post by swoody on 2009-07-24
> **Sef said:**
> Amsn has web cam support.

I would recommend Amsn as well. I don't use it anymore, but it did a great job at doing what I needed it to do :)

---

### Post by 3rdalbum on 2009-07-24
> **frunns said:**
> Isn't it easier just enabling PAE?

It's easier still to just install the 64-bit distro :-)

---

### Post by wizard10000 on 2009-07-24
> **frunns said:**
> Isn't it easier just enabling PAE? Can't remember the exact steps, but compared to a reinstall, of the server version no less, I'd recommend doing it manually if there really is need for it.

No need to reinstall anything - just install a server kernel.

---

