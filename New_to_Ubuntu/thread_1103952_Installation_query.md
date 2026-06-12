---
title: "Installation query"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by expaddy on 2009-03-23
First of, Hi all,

I am currently running vista 64bit and I want to eventually switch to linux. In the mean time I have a 500gig drive which at the moment contains 2 partitions. The first partition is 100G and the rest is used for storing files. I want to install Ubuntu on a resonably big parttion becasue I would like to try it out for virtualisation purposes. 

So when I resize the partitions and install Ubuntu, will i still be able to access my files and programs on the second partition. My intention is to take 20G from the first partition and 30G from the second leaving me with 50G for Ubuntu. One problem I can see is that from what I have read so far the swap file needs to be 2x ram, well I am currently running an 8G system so can I reduce that or is it open to take a different size and still operate ok.

Finally does anyone have experience installing Ubuntu on a 64bit system.

Well in the meantime I will wait for the full back up to complete and do some more studying.

---

### Post by halitech on 2009-03-23
20 gig should be fine for / and you can use the 30 gig for /home, just make sure you use the manual partitioning scheme when you install.

as far as seeing the windows files, no problem there at all. Linux can read windows files fine, going the other way could be a problem though without third party software.

for the ram, if you have 8gig, set your swap at 1 gig as it will hardly be used with that much ram.

64bit used to be a pain but its gotten better from what I have heard.

good luck and welcome to the forum

---

### Post by PenguinsFan on 2009-03-23
Hi There,

Thrilled your considering trying Ubuntu!

It would be easiest to take all of the space from the 2nd partion if at all possible - it would be faster to do this reallocation and also easier to undo in the future if you ever decide to. You might want to consider a dedicated partioning application like [Parted Magic]("http://partedmagic.com/") to do this, but you could also do it from the Ubuntu CD. Let me know if you need any additional help with this process!

And I have used 64 bit Ubuntu - its a wonderful operating system! The installation is very easy (no harder than 32 bit) and performance is very good. There are some on this board wo question the stability of Ubuntu 8.10 @ 64 bit but I've never experienced a problem. If you'd rather try the older version (8.04) thats always an option too (post if you have questions on locating the old edition) but if I were you I'd just jump straight to 8.10.

Hope this helps!

---

### Post by expaddy on 2009-03-23
Thanks muchly for the replies.

@PenguinsFan, I will probably do something like that in the future but at the moment I would like to have both oses installed and running and give both access to the files partition.

I will have a look at Parted Magic but I am currently looking into gpart to create the partition before I load as it looks like a nice tool.

As for Ubuntu 8.1 64 bit being buggy it can't possibly be any more buggy than vista 64bit :rolleyes::rolleyes:

So is the swap file pretty much like doze then and can you do without a swapfile. I don't currently use one in Vista.

Another question while I'm at it. Can you have virtual machines stored on another partition than Ubuntu, i.e. an NTFS partition and still use them on VMware from within Ubuntu.

---

### Post by thehouseofho on 2009-03-23
Hey there expaddy.  I run XUbuntu with VMWare installed and I can say you can definitely run images from an NTFS partition.  However, there are issues with taking snapshots of images, so you will need to be mindful of that.

Also, have you thought about installing Ubuntu within Windows as an application using wubi?  It's one of the installation options.  It's a very simple install which does pretty much all of the work.  The great thing about it doing all the work is that you can check out the configuration settings and learn more about things like swapfiles and memory management once Ubuntu is installed as opposed to trying to figure it out one the fly.  Also, since it's an application within Windows, if you do any damage to the Ubuntu OS, you just have to reboot into Windows and uninstall it from add/remove programs.

Just thought it would be a nice way for you to slowly migrate from Windows to Ubuntu.

---

### Post by expaddy on 2009-03-23
Hi thehouseofho,

It probably would be an easier way to install, but hey easy is never fun in the IT world.

I have decided on using a parted magic live cd and pinching space of the exsisting file partition. So it should leave the Vista partition alone.

I am glad to hear about the vm files still being accesible if I store them on an NTFS partition from within Ubuntu. That way my Ubuntu install can be a lot smaller.

I will report back once it's complete and let you know how it goes, thanks for all the help and of course the very warm welcome. I'm enjoying this linux malarkey already.

---

### Post by expaddy on 2009-03-24
Well all went ok, (nearly).

I used gpart and made partitions according to a doc I found somewhere,

ext3 /
swap
ext3 /home
ext3 /data

As I said all went well and the install went a treat, although gpart really took its time resizing and shrinking one of my partitions, but I suppose its doing a lot of work so thats to be expected.

The only problem that I now have is that when I try to give ubuntu a static address it wont connect to the internet but will when I run it automatically from my routers dhcp server. Probably something I'm not quite familiar with just yet.

Anyhoos onward and upward.

As for ubuntu, at a first glance I have to say I love it, but then again coming from trying to get vista 64bit running sweet I'm easily impressed.

On the whole it looks good and is well and, for a change from windows, logically laid out. I think I'm going to enjoy this.

---

