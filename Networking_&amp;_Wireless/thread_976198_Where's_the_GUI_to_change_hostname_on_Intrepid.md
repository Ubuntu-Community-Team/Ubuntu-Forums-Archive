---
title: "Where's the GUI to change hostname on Intrepid?"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by greatwolf on 2008-11-09
Hi all,

The title says it all. Does anyone happen to know?

Thanks

---

### Post by greatwolf on 2008-11-09
*bump*

---

### Post by damianpeterson on 2008-11-09
**bump**

---

### Post by damianpeterson on 2008-11-09
Sorry about the previous bump; I've just read elsewhere that bumping is poor netiquette and it wasn't my intention to be an ***.

(I also realise that this apology probably counts as a minor breach too - arrgh, the dilemma!)

---

### Post by jobix on 2008-11-09
I don't know about the GUI method, but you could just edit the /etc/hostname file. Open up a terminal, open your favorite editor, and edit the /etc/hostname file to whatever you want.

---

### Post by greatwolf on 2008-11-09
> **jobix said:**
> I don't know about the GUI method, but you could just edit the /etc/hostname file. Open up a terminal, open your favorite editor, and edit the /etc/hostname file to whatever you want.

Thanks for the reply. I am aware of this method but if I do it this way I also have to remember to change the hosts file as well or it'll screw up my sudo ability.

I'm looking for a GUI method because I'm hoping that changing it through that will keep the hostname persistent across reboots on my liveusb. And also secondly to avoid that pitfall of not editing hosts. Besides, previous release of ubuntu had this via System->Admin->Network and settings. Why would the latest release take this out?

Thanks

---

### Post by jobix on 2008-11-11
I see what you're saying. I checked Hardy and that System->Admin->Network and Settings feature is still there. So, I don't know why it's not there in Intrepid. Maybe try updating? 

In the meantime, you could just write a shell script to do the updates for you. Something like this:

> cp hosts hosts.orig
sed "s/oldname/newname/" hosts > hosts.tmp
mv hosts.tmp hosts

Similarly, for any other files.

---

### Post by Mirzabah on 2008-11-17
Open up a terminal window and type:

```
sudo aptitude install gnome-network-admin
```

Now you can open up the network administration tool from **System > Administration > Network**. The hostname setting is under the **General** tab.

---

### Post by greatwolf on 2008-11-19
Thank you!
I'll have to give that a try later. I knew there's a method to do this.

---

### Post by magicfab on 2009-10-06
In jaunty you can install gnome-network-properties, then run network-admin to get the same tool.

---

### Post by Francewhoa on 2010-03-12
There is an **easier, safer and faster** way to do this at [http://ubuntuforums.org/showthread.php?p=8955992#post8955992](http://ubuntuforums.org/showthread.php?p=8955992#post8955992)

---

### Post by COKEDUDE on 2010-06-11
> **magicfab said:**
> In jaunty you can install gnome-network-properties, then run network-admin to get the same tool.

Does that tool still exist?

---

