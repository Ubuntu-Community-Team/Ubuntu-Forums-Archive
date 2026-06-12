---
title: "Borked Wubi Installation"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by MIJester on 2010-01-02
Hello all.  It is nice to be venturing back into the FLOSS world.  I have only dabbed the tip of my toe in over the past many years so getting the terminology and CLI verbiage correct is taking some time.

So here is how I borked my system.

I have a wubi install of Karmic but forgot to expand my partion to a large size.  Using the WubiGuide, I created a new 100GB virtual partition to add to they system.  When I attempted to mount it, I got a message that it was not included in the fstab.  I added a line in it based on the first line.  I can't read it right now (since this is a dual boot system) but it went something like:

/host/ubuntu/disks/extra.disk /  ext3 (something, something, etc..)  

Basically I know that by not mounting it someplace other than / I borked it.  It shouldn't be an issue, but now when I try to boot and it goes to the recovery prompt I can't edit the fstab file.  I get that it is read only but looged in as root it is (rw-r--r--).  I tried

chmod o+w fstab -v 

I get an error that it is unable to change the properties of the read only system file.  I tried it with sudo (which is a little repetative reduntant since I was already root) and tried looged in with my ID and sudo.

I even tried chmod e+w fstab and have the same issue.  Any help?

BTW:  If anyone needs to do this in the future, be smart and use Wubi-add-virtual-disk addon and the command:
sudo sh wubi-add-virtual-disk /home 100000

Jester

---

### Post by J V on 2010-01-02
hmm...

dont remember much bout fstab, but try this:

/host/ubuntu/disks/extra.disk /media/test  ext3 something something whatnot

---

### Post by MIJester on 2010-01-02
Thanks.  The big issue I am having is not being able to edit the file.  chmod doesn't seem to be letting me change the attribut so that I can save the file.

I will use your syntax when I can finally save the change.  I wasn't sure of the proper mount point once I could edit it.

---

### Post by J V on 2010-01-02
Well if you want, I suggest mounting it at /home and moving all your stuff over...

Remember that wubi installs are generally nastier than normal ones :P

I don't know what the permissions problem is, recovery should make you root (and give you access to the file) so you can edit it... Perhaps the recovery root is a different one and doesn't have perms to change the file...

try using chmod 777 and then reverting to 444 after (forgot the letter chmods...)

Edit: letter chmods are a+w

---

