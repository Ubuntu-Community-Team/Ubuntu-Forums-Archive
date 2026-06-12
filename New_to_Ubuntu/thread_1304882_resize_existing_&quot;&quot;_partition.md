---
title: "resize existing &quot;/&quot; partition?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by duds2008 on 2009-10-29
Hello people, I hope this finds you all well.

I am trying to upgrade to 9.10 from 9.04 using update-manager -c. However, because I manually partitioned 9.04 (/ partition 10 GiB) the upgrade process is complaining that there is not enough free space to perform the upgrade to 9.10. I have run sudo apt-get clean and emptied trash, but to no avail. It still complains. I know I can probably remove a whole load of packages to create free space but think this is a bit of a drastic measure. Is there any way to resize an existing "/" partition, to make it bigger? I don't really want to do a clean install. Any help/suggestions are sincerely appreciated. Thank you in advance.

Dudley.

PS: Good luck with 9.10. I test drove the beta release (on another computer) and was well impressed!

---

### Post by kellemes on 2009-10-29
Download/Burn/Boot [Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php") and resize the partition..
Always assume trouble, so backup!

---

### Post by duds2008 on 2009-10-29
Thanks kellemes! I know that using a live cd is an option, but am wary of using it. As you suggest, loss of data is a possible outcome! I am more looking for some sort of (at the risk of sounding ridiculous) stable way of performing this operation! Thanks anyway! Will consider it an option, should all else fail:)
Dudley.

---

### Post by ikisham on 2009-10-29
Clear the contents in /var/log and subfolders my help you too. But I don't know if that's completely safe (in regards to the update) so someone may answer this.

---

### Post by duds2008 on 2009-10-29
Thank you ikisham. I will try that. Though it says I need around +- 2.9GiB free space to perform the upgrade. I don't think that the system log files will release that much space. That is however a good suggestion. Thanks! I will try it.
Dudley.

---

### Post by kellemes on 2009-10-29
> **duds2008 said:**
> Thanks kellemes! I know that using a live cd is an option, but am wary of using it. As you suggest, loss of data is a possible outcome! I am more looking for some sort of (at the risk of sounding ridiculous) stable way of performing this operation! Thanks anyway! Will consider it an option, should all else fail:)
Dudley.

There are ways to clean up your system, that is.. removing files you don't need and such.. That way you can obviously regain some space.
But even then you have a risk of data-loss ;-)
I'm afraid there is no 100% safe way of doing this.

---

### Post by duds2008 on 2009-10-29
I don't have anything really important on my machine. Nothing life threatening ( though I haven't watched Disney's "up" movie yet:) ). I guess I could perform a clean install. I have just really become sentimental in regards to how long I have had my current OS installed! The live cd method is starting to look more and more appealing to me! :)
Thanks for the suggestions so far!
Dudley.

---

### Post by duds2008 on 2009-10-29
I have an idea. Would it be possible for me to download 9.10 and install it side by side with 9.04? That way I can see if it is as good as it seemed to me (when I tried the beta version of it) This will also allow me time to perform my backups. (There are after all only 2 types of people in this world: those who perform back ups, and those who wish they had!)   :)

---

### Post by ikisham on 2009-10-30
Of course you can install it side-by-side, as long as you have space to create a new partiton for it (it'll use the same swap space). Minimum reccomended is 6GB (you can install in less space but if you like it, better go with a proper amount).

---

