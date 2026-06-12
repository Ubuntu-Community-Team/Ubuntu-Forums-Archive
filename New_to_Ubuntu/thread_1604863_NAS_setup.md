---
title: "NAS setup"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by triemba on 2010-10-24
I've only just recently moved into using Ubuntu (using version 10.10). I am using Windows 7 still on one computer (a laptop), but have installed Ubuntu on my desktop and a netbook. It has been a good experience so far, and answering this question may enable me to convert the laptop as well...

I have a D-Links DNS-321 NAS setup to a LinkSys router. The NAS holds two drives (500GB and 1.5TB). I would like to know how to have the NAS drives automatically mount (or would it be map???) in Ubuntu.

Right now, I am accessing the drives by going to Places --> Connect to Server, selecting Windows Share, and entering in the server address 192.168.1.101; the only issue with this is that I have to do it each time I want to access the NAS.

I am quite sure that this is a question that has been asked before, but any help would be appreciated. Thank you in advance.

---

### Post by ShakeyJake on 2010-10-24
Once you've accessed the drive, just bookmark it Nautilus. Click Bookmarks>Add Bookmark. That way you'll always be able to get at it by just clicking on 'Places'.

There are many more sophisticated ways to actually map it, but why bother if all you need is access to the files?

---

### Post by ArgusVision on 2010-10-24
I'm pretty sure you can add a /etc/fstab entry to handle that. I don't remember the exact syntax, but it's basicly

ipadress/pathto/directory /mount/path fs_type

I know it's not an exact answer, but I hope it's enough to get you started on the right search.

---

### Post by triemba on 2010-10-25
Thank you both. I have the NAS drives bookmarked now. However, I am not sure if bookmarking provides the same functionality as mapping (such as having an automatic backup perfomed to the NAS, for instance). Also, I am very new to using the terminal and entering scripts. If I had step-by-step for performing those entries, or if I can be pointed in the direction of a package to download to handle it, that would be great.

---

### Post by Paqman on 2010-10-25
> **triemba said:**
> If I had step-by-step for performing those entries, or if I can be pointed in the direction of a package to download to handle it, that would be great.

[Here you go]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").

A permanent entry in /etc/fstab is definitely the best way to do this. Once it's set up it'll be very easy to use.

---

### Post by ArgusVision on 2010-10-25
Thank you Paqman.

---

### Post by triemba on 2010-10-25
Paqman, many thanks.

---

