---
title: "Dualbooting xp and ubuntu"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by RobMcL on 2010-04-04
I'm thinking of getting a new netbook over the summer, the [new dell mini]("http://www1.ca.dell.com/ca/en/home/Laptops/inspiron-1012/pd.aspx?refid=inspiron-1012&s=dhs&cs=cadhs1&ref=lthp") 10 to be exact. What I want to do is have ubuntu on one partition, xp on the other, and the rest of my data (music, pictures, documents etc.) on the other. That way, I will be able to access it on both xp and ubuntu. What I want to know is if I can get ubuntu to make the default folders in another partition (for example, if I go to places>music, it'll open the folder in my data partition).

     I have a little bit of experience in ubuntu (virtual machines and wubi), so the less terminal, the better.

---

### Post by BrokeMahPC on 2010-04-04
What you are proposing could cause you problems. If I were you I would decide which OS you would use most of the time. Eg: I use Ubuntu for almost everything and boot into windows occasionally to play games or use Itunes.
Windows and Ubuntu use different file systems to format their partitions:
Windows - NTFS
Ubuntu - Ext3 or Ext4 (latest versions Ext4)

Windows cannot use Ext3 or 4, but Ubuntu can use NTFS. Places - Music is in your /home folder or partition which is Ext4. I'm not sure if it is possible or a good idea to have a /home partition in NTFS, probably NOT!

You could have a separate data partition where you want to keep things available to both OS's but it will have to be formatted in NTFS for windows to use it. But, the Places options would not work as you want them to. The partition would be listed under places where you would have access to it. (In 9.10 Karmic you would have to enter a password unless you automount it at boot., !0.04 Lynx lets you in without a password)

You can edit fstab to automount the partition at boot but you would have to research that and decide if it's within your expertise. There is a GUI for doing that called PySDM that is simple to use.
Look here: [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)
Windows would see the data partition automatically and assign it a drive letter in the usual way.

Trying to keep a common data partition organized and up to date can be a headache in itself as you have to decide all the time if you want windows to have access to certain files and remember to move them to the data partition from /home.

Hope this helps, as you can see you have to know precisely how you are going to use your PC and which OS you are going to use for what. You need a plan I guess!

---

### Post by Sin@Sin-Sacrifice on 2010-04-04
Yeah... make your data partition ntfs and move /home/username/folder_you_want to the ntfs partition. For me the links in menus followed where I moved it automagically (Karmic and Lucid). If it doesn't for you then you can change the location using the link's properties (right click it).

---

### Post by ronnielsen1 on 2010-04-04
I see you're new here. I propose you treat Ubuntu as the main OS because it's only a matter of time (about 5 months) before you start thinking that Windows is just taking up space. Make a folder in a partition that you want  to share  (ext3)  Then  install  Ext2IFS  for  Windows.  [http://www.fs-driver.org/](http://www.fs-driver.org/). Then when you decide you no longer need Windows you can just move the little slidey thing over in gparted and you won't lose any files.

---

### Post by oldfred on 2010-04-04
I directly mount my shared NTFS parition into /home but link data files from another ext3 /data partition into home. I like setting up firefox and thunderbird to use the same profile in windows and linux so my bookmarks and emails are the same. As mentioned above I am now mostly in Ubuntu and now most of my data goes into ext3 data partitions.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Linking linux folders into /home
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
h

---

### Post by RobMcL on 2010-04-04
Thanks for the advice guys. The only reason I'm keeping xp is in case something doesn't work with wine (maybe a specific program for school), and in case I don't like ubuntu I'll have something to fall back on (though I highly doubt this'll be the case). I'll look into your suggestions. Again, thanks.

EDIT: Quick question, would it be a good idea to have my data on a separate partition if I'm only using ubuntu? That way if I mess something up and have to reinstall it, or I use another linux distro, all my data will still be fine.

---

### Post by spiky001 on 2010-04-04
Yes that is a good idea that is how I sent mine up

---

