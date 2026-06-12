---
title: "Xubuntu  CD- quickest way to get reliable one"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by collards on 2009-12-04
Hi

turns out that I may need Xubuntu for my older PC instead of Ubuntu.

what's the quickest way to acquire one?  I googled and found a couple of sites but would like to know the quickest & most reliable to get one.  

any experience/resources to share?

Help please & thank you

Collards

Collards.

---

### Post by mkvnmtr on 2009-12-04
Download by torrent.

---

### Post by collards on 2009-12-04
Thanks, 

please explain torrent.

I installed Ubuntu over the weekend but am unable to use Update Mgr. to do the first big  set of updates and the program is behaving erratically.

I have tried to down load a couple of things and it wouldn't work

C

---

### Post by kansasnoob on 2009-12-04
What version of Ubuntu did you install?

Are you able to run the Live CD, that is by choosing Try Ubuntu without changes to your computer?

How fast is your internet?

Is Ubuntu the only OS on this machine, any other data partitions?

If you can run the Live CD please post the output from terminal of:

```
sudo fdisk -l
```

BTW that's a lower case L.

Basically what I'm thinking is you might be able to mount and chroot your Ubuntu install and convert it to Xubuntu as described here:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

General info about mount and chroot here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

But if you have a slow internet connection that might stink! And if Ubuntu is really already "broken" it might not work at all!

---

### Post by kansasnoob on 2009-12-04
I was just thinking here. That can sometimes be dangerous :p

Maybe we should try and troubleshoot the problem with Ubuntu. Instead of trying to update with Update Manager I'm curious what happens when you go to Terminal and run:

```
sudo apt-get update && sudo apt-get upgrade
```

If a previous update was interrupted you may need to run "sudo apt-get clean" and "sudo apt-get -f install".

Then again if you can't use Firefox to browse then maybe it's a networking issue (which I'm woefully clueless about because I've never had such an issue).

---

### Post by Terl on 2009-12-04
Collards:  Define "older pc" please.  What are the specs?  Could be that is some of the issue with Ubuntu.

---

### Post by kansasnoob on 2009-12-04
> **Terl said:**
> Collards:  Define "older pc" please.  What are the specs?  Could be that is some of the issue with Ubuntu.

+1! I didn't think to ask that.

---

### Post by collards on 2009-12-08
Hi, sorry about the long delay in responding.

I am on different ( &refurbished) computer now with Ubuntu installed--yaay!

---the other computer  finally developed more desktop problems that wouldn't allow me to use the menu at all or do anything!  

About the other computer--I've gotten lot's of very helpful advice in another thead-- but haven't been able to use that advice yet. 

The computer is a Dell Dimension L700CXE with 512 RAM & 700 mhz.  Ubuntu partition is more than 12G.

Thanks,
collards

---

### Post by heyho on 2009-12-08
You should be able to run Ubuntu with those specs but it won't be nippy.  I wouldn't expect Xubuntu to be much faster if at all.

By all means give it a go, but something like puppy would really rejuvenate  it.

And can't you just download directly from the Xubuntu site?

---

### Post by LeifAndersen on 2009-12-08
I have heard that the up and coming LUbuntu is much faster for older hardware, you may want to give that a try.  However, I think that the only way you will be able to get that is by downloading and burning it yourself.

---

### Post by collards on 2009-12-09
Thanks everyone,

Had my specs checked out last night by a Ubuntu-user tech person and he believes (as others in this forum have told me) that my video card resources are simply eaten up by Gnome desktop/windows manager.  we are going to install Xubuntu on it next week so that I can use the lighter XFCE desktop....and see what happens.

I will post results here or in another thread for those who may be interested.....

I will also do a search on Lubuntu to see what that is like.


Thanks again.

---

