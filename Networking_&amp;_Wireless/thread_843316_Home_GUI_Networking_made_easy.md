---
title: "Home GUI Networking made easy"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by fgranlun on 2008-06-28
Hi all,

I'm a beginner to Ubuntu. Not a complete noob, but almost.

I have five computers at home, in different rooms. I also have a network attached storage device with 1 TB of disk space. There's no central server, it's just all connected through my home router. They all share the same Windows domain name - "WARLORD".

I'd like to connect my Ubuntu laptop to the rest of the computers. All of them have at least one shared folder - some of them more. And I'd like to access my NAS drive.

There's a lot of talk about Ubuntu easy of use, but at the same time a lot of threads concering configuration file editing and such.

I'd like to skip all that, if possible.

Is there an easy, GUI way to just map the different shares as drives (as in Windows) or just plainly access them (like in MacOSX)? When I try I get a lot of different problems. Some shares show, some don't. I can for the most part access family photos, but not play AVI files (without copying them to my Ubuntu laptop first).

So, briefly: How do I map shares as drive letters (or equivalent) with as few as possible mousecklicks? I do not want to edit any configuration files. I stopped doing that in Windows when Win95 was released. :-)

Please help.

// Fred

---

### Post by bobyy on 2008-06-29
Hy there ...
You can do all this but you must install samba and smb4k(a gui tool for samba to manipulate shares).
Ewrithing can be istaled via synaptic or apt-get
Regards.
(checkout forum about Samba)

---

### Post by fgranlun on 2008-07-01
Hi,

Thanks. I've tried it. It installs horribly on Ubuntu since it uses KDE. And nothing I do seems to have any effect on anything. Also, there are thousands of checkboxes, variables and stuff I cannot even begin to comprehend.

In Windows I click on "My network", then on the shared volume I want to access, and can then right-click and choose "map network drive". Three steps, no third party program downloads, just click-click-click-done.

Is there no Ubuntu equivalent?

Let's say I've wrote an article in Openoffice, and need to save it on a SMB network drive to deliver it to the publishing desk. Isn't there an easy, 20 second, way to do that?

Please help!





> **bobyy said:**
> Hy there ...
You can do all this but you must install samba and smb4k(a gui tool for samba to manipulate shares).
Ewrithing can be istaled via synaptic or apt-get
Regards.
(checkout forum about Samba)

---

### Post by bobyy on 2008-07-01
Hy Fred.
Somevere in this forum is a how to about that ...but since i vas not interesed and idont know where is it...sorry ...try to search in forum.
It seems to be not so easy with sharing stuff in linux ...
maybe i am whrong :)...but it is my fault ..ha ha ha  :) because i use for years just FTP ..

---

### Post by bobyy on 2008-07-01
Hmmmmm ....Fred ...
i think this is what you are searching....

[http://mixeduperic.com/index.php?option=com_content&task=view&id=71&Itemid=46]("http://mixeduperic.com/index.php?option=com_content&task=view&id=71&Itemid=46")

i am right???

---

