---
title: "Permissions issue with former boot drive"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by trooperchix on 2009-09-17
My other computer bit the dust (fried, like chicken) but the hard drive is still ok. I am using my other laptop to pull the data off the first hard drive from my now fried laptop, and I'm getting permissions issues. I have the old hard drive now in an external hard drive enclosure hooked up to my laptop via usb. I used to be able to connect via wi-fi and exchange information between the two laptop systems fine before it fried. I figured I could just take that old hard drive in an enclosure and take the information off as I am afraid since the laptop fried that this hard drive may fry as well. So I'm trying to save my data. How do I change the permissions on the chicken-fried hard drive now that it is no longer the boot drive? Please be as detailed as possible. I'm a dyed in the wool ubuntu user now, but don't have the skills I used to with winblows.


Oh, and just so you know, the chicken-fried laptop was due to overheating. A Dell system poorly designed that are no longer in production because of the heat issue (as in burn your skin holding it, bad heat management). Heat isn't a happy thing for a hard drive, so I'm taking precautions...

---

### Post by undecim on 2009-09-17
It seems to me that you have a different ID between the external drive and you other computer. (i.e., one was the first user added (#1000), and the other is the second (#1001) or a similar situation)

All you need to do is run this in a terminal:

```
sudo chown -R username:username  /path/to/files/on/external/drive/
```where username is your username on the working computer and /path/to/files/on/external/drive/ is the path to the files you are having permission issues with.

This will make you the owner of all the files in that path on the portable hard drive

---

### Post by LewRockwell on 2009-09-17
alternately you can use a different *nix distro

we use Puppy Linux LiveCD as our first attempt to rescue data

.

---

### Post by trooperchix on 2009-09-17
> **undecim said:**
> It seems to me that you have a different ID between the external drive and you other computer. (i.e., one was the first user added (#1000), and the other is the second (#1001) or a similar situation)

All you need to do is run this in a terminal:

```
sudo chown -R username:username  /path/to/files/on/external/drive/
```where username is your username on the working computer and /path/to/files/on/external/drive/ is the path to the files you are having permission issues with.

This will make you the owner of all the files in that path on the portable hard drive

Ok, so I get the first part, now the /path/to/files/on/external/drive/

I know spaces are handled differently.  how would I write this if the following is true:

/media/disk/home/dawn/Desktop/     and the folder's name is 
This will make you the owner of all the files in that path on the portable hard drive[/QUOTE]

Ok, so I get the first part, now the /path/to/files/on/external/drive/ is different on this one because I know spaces are handled differently.  The path would start as 

/media/disk/home/dawn/Desktop/    

and the folder is "Jump Drive Backup" 

and the actual file is (and this is correct) "Paragon report November  2008.xls"   yes, two spaces between "November" and "2008".  How do I code that?  

My boss is going to have my keister if I don't get this report fixed...

---

### Post by LewRockwell on 2009-09-17
> **trooperchix said:**
> Ok, so I get the first part, now the /path/to/files/on/external/drive/ is different on this one because I know spaces are handled differently.  The path would start as 

/media/disk/home/dawn/Desktop/    

and the folder is "Jump Drive Backup" 

and the actual file is (and this is correct) "Paragon report November  2008.xls"   yes, two spaces between "November" and "2008".  How do I code that?

use quotes to "contain the broken_with_spaces file names" {{cheesy grin}}

[http://www.netmechanic.com/news/vol6/html_no6.htm](http://www.netmechanic.com/news/vol6/html_no6.htm)

.

---

### Post by undecim on 2009-09-17
> **LewRockwell said:**
> use quotes to "contain the broken_with_spaces file names" {{cheesy grin}}

[http://www.netmechanic.com/news/vol6/html_no6.htm](http://www.netmechanic.com/news/vol6/html_no6.htm)

.

You can also use the backslash character "\" to escape spaces and other special characters (for example, a quote character withing a quoted filename, or if you have already typed the file path and don't want to go back and add quotes)

example: cat /home/undecim/crazy\ file\"name\"\{\second\}

would show the contents of the file: /home/undecim/crazy file "name"{second}

---

### Post by trooperchix on 2009-09-17
Now how do I do this for the entire home file?  I have access to a lot of it, but other things I do not.  I need to backup everything on that drive...

thanks guys..

---

### Post by undecim on 2009-09-17
just use the home folder as the path to file in

chown -R username:username /path/to/home/folder/

The -R means "recursive" which operates the command on every file and folder within the folder you run the command on. (i.e. then entire folder)

---

### Post by trooperchix on 2009-09-17
thanks guys!

---

