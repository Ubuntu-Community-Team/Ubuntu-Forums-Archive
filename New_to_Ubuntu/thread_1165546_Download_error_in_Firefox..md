---
title: "Download error in Firefox."
date: 2009-05-20
forum: New to Ubuntu
---

### Post by xavierp94 on 2009-05-20
Everytime I want to open a file from Firefox in Ubuntu I get the the attached error message. I've tried to chmod my tmp directory to 777 but it only work once then it keeps on doing the same thing again. Does anyone have any solutions? I'm running Ubuntu 9.04.

[[IMG]http://img194.imageshack.us/img194/7226/screenshotdownloaderror.th.png[/IMG]]("http://img194.imageshack.us/my.php?image=screenshotdownloaderror.png")

---

### Post by Miljet on 2009-05-20
Is there some particular reason to save in /tmp directory?

Try creating a /home/your_name/temp directory in your home  and saving the files there.

---

### Post by xavierp94 on 2009-05-20
> **Miljet said:**
> Is there some particular reason to save in /tmp directory?

Try creating a /home/your_name/temp directory in your home  and saving the files there.
I didn't create that directory. It's the default when I started using Ubuntu.

---

### Post by zeroseven0183 on 2009-05-20
Consider changing the downloaded files directory.

In Firefox, click on **Edit > Preferences** then change the directory under **Downloads**

I have a separate folder created only for downloads. I'm sure you're more creative than I am.

---

### Post by Miljet on 2009-05-20
You can also click the button for "Always ask me where to download files."

Normally Firefox defaults to downloading to your Desktop unless it has been changed.

---

### Post by xavierp94 on 2009-05-20
> **Miljet said:**
> You can also click the button for "Always ask me where to download files."

Normally Firefox defaults to downloading to your Desktop unless it has been changed.
Ok, the problem isn't that I cannot open the files once I save them. I can do that perfectly. My default location is in the Desktop folder. The problem is when I open an attachment such as a doc file but I don't want to save it so I make it open directly to Openoffice I get that error message. Thanks for trying to help though. :(

Edit: Here is a screenshot.
[[IMG]http://img156.imageshack.us/img156/5233/screenshotbco.th.png[/IMG]](http://img156.imageshack.us/my.php?image=screenshotbco.png)

---

### Post by zeroseven0183 on 2009-05-20
How about the longer step? Open the containing folder and then double-click the file.

---

### Post by Java Geek on 2009-05-20
From the looks of your picture, it seems that OpenOffice may be broken...Try a different processor like Abiword to be sure

---

### Post by xavierp94 on 2009-05-20
> **zeroseven0183 said:**
> How about the longer step? Open the containing folder and then double-click the file.
Why do that when there is a faster option?

---

### Post by xavierp94 on 2009-05-20
> **Java Geek said:**
> From the looks of your picture, it seems that OpenOffice may be broken...Try a different processor like Abiword to be sure
I believe that may be a possible problem. I tried uninstalling Openoffice and it told me that I couldn't because the packages were broken.

---

### Post by Java Geek on 2009-05-20
Then try uninstalling the packages with Synaptic Package Manager and then reinstall.

---

### Post by zeroseven0183 on 2009-05-20
Consider upgrading it to 3.1.

> Why do that when there is a faster option?
Troubleshooting

---

### Post by xavierp94 on 2009-05-20
> **zeroseven0183 said:**
> Consider upgrading it to 3.1.


Troubleshooting
Isn't the new already on the repositories? I've reinstalled the suite from the Add/Remove and I'm still getting the same problem.

---

### Post by Java Geek on 2009-05-20
Is it an option to open it in any OTHER word processers (just so that we can narrow down the problem)

---

### Post by zeroseven0183 on 2009-05-20
> Isn't the new already on the repositories? No. You need to add OOo 3 repositories to your sources list.

I found a very helpful site which shows the steps in upgrading to 3.1 in Jaunty. Check this out: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

---

### Post by xavierp94 on 2009-05-21
> **Java Geek said:**
> Is it an option to open it in any OTHER word processers (just so that we can narrow down the problem)
I've tried with Abiword and it works great. I don't know why it won't work with Openoffice.

EDIT: I think I may have found a bug. I reinstalled Ubuntu and I still get the same problem. I try downloading a doc file directly to open office and it does not work.

EDIT 2: Seems that it only happens with only the document I was trying to download.  I think I solved it.

---

