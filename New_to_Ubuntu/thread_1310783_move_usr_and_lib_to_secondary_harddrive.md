---
title: "move usr and lib to secondary harddrive"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by zerominded on 2009-11-02
i've been doing a lot of reading on here and found most of my answers.  i was actually able to go from windows to 7.04 to 8.04 to 8.10 and now finally to 9.04.  i do have one question.  ive been doing extensive research and cant find the answer.  heres my question:  i currently have an asus 900 eee pc.  it has a 4gb and a 8gb harddrive built in.  is it possible to move the contents of /usr and /lib to this secondary harddrive, and make sure the computer always references it there?  i still have space available on the 4gb, but would like to free a little more.  i looked through gparted and was attempting to change it from /meda/sdb1 to /usr, but was nervous about messing something up.  i am picking everything up pretty quick, but you'll just have to put it in easy terms.  thanks in advance and keep on keepin on

---

### Post by scorp123 on 2009-11-02
**/usr** could be on its own mount-point, yes ... but **/lib**: **[COLOR="Red"]NO.[/COLOR]** It's needed during boot. Just like **/etc**, **/sbin** and **/bin**, **/lib** [COLOR="Red"]**MUST**[/COLOR] remain on the **"/"** partition.

---

### Post by zerominded on 2009-11-02
thats good to know.  internet is crazy slow and i cant sit through an all nighter to upgrade again if i messed up my /lib.  if i use gparted to use my secondary harddrive as /usr, do i just change the mount point?  i dont want to accidently make it like /usr/sdb1.  i only want it recognized as /usr.  also, once i do figure out how to change it, will all the items currently in /usr be automatically moved, or do i need to back them up, then move them after changing the mount point?

---

### Post by philinux on 2009-11-02
You probably dont to do anything other than housekeeping. Check roots trash and clear out the apt cache.

sudo apt-get clean, autoclean, or auto remove etc. Have a look a at ```
man apt-get
```

---

### Post by zerominded on 2009-11-02
> **philinux said:**
> You probably dont to do anything other than housekeeping. Check roots trash and clear out the apt cache.

sudo apt-get clean, autoclean, or auto remove etc. Have a look a at ```
man apt-get
```

unfortunately i already did all of that.  went over a few howtos and cleaned everything.  i have about 500-600 mb free.  i know thats plenty of space, however im doing a lot of playing around with programs and games and what not.  im a beginner so the best thing for me to do is just play around.  plus, i have all of this space on my second hard drive that is not getting put to use.  i have two externals that i use for all media and files.  just trying to take advantage of both OB harddrives.

---

### Post by philinux on 2009-11-02
If you got a 4 gig and an 8 gig then it would make sense to have the distro on the 8 gig drive.

---

### Post by zerominded on 2009-11-02
> **philinux said:**
> If you got a 4 gig and an 8 gig then it would make sense to have the distro on the 8 gig drive.

yeah.  i already thought about that.  i might try that when i get back from this deployment in a few weeks.  i was just looking for a solution so i dont have to reinstall any distros until i get home

---

### Post by philinux on 2009-11-02
> **zerominded said:**
> yeah.  i already thought about that.  i might try that when i get back from this deployment in a few weeks.  i was just looking for a solution so i dont have to reinstall any distros until i get home

Yep, mind you if you got 600meg free and you keep up the housework ;) you'll survive.

---

### Post by barthel on 2009-11-02
I've got to dash off to work, but here's a quick how-to, assuming your 8GB drive is empty and already formatted and visible as a Linux fileystem--and that you want it to only contain /usr.

Another quick assumption: 4GB is /dev/sda1 and 8GB is /dev/sdb1.

Copy /usr to the new drive:
sudo cp -a /usr/* /mountpoint (where /mountpoint is whereever the 8GB drive is mounted)

Edit /etc/fstab as root with your favorite editor and add the following line:
/dev/sdb1 /usr ext3 defaults 0 2
(If there's already a line for your 8GB drive, copy it, change the mountpoint to /usr, and comment out the original [as a backup]). [You may want to make a backup copy of /etc/fstab first.]

For safety, until you reboot and verify it's working:
sudo mv /usr /usr.old

Create a new /usr for your mountpoint:
sudo mkdir /usr

After you reboot and are sure everything works, you can safely delete /usr.old

Oh--if your 8GB drive isn't empty, you could simply make it a symlink, like so:
sudo mv /usr /mountpoint
sudo ln -s /mountpoint/usr /

Hope this helps--but please remember that what I gave you above is pseudocode--you'll have to modify the commands to match your actual system.

---

### Post by zerominded on 2009-11-02
> **barthel said:**
> 
Oh--if your 8GB drive isn't empty, you could simply make it a symlink, like so:
sudo mv /usr /mountpoint
sudo ln -s /mountpoint/usr /



do not do this.  im lucky i had a live cd to move /usr back to its rightful place.  i had lost everything, even sudo commands.  note to self, install to 8gb next time.  thank you everyone for your help!!!

---

### Post by barthel on 2009-11-02
Sorry--I should have simply told you to do the "surgery" while running from the live CD...

That's what I get for trying to be helpful before dashing off to work.

*Aha!*
The reason you lost 'sudo' is because it's under /usr/bin.

Either using a root terminal (`sudo su`) from the beginning or an explicit path to sudo (`/mountpoint/usr/bin/sudo`) after the `mv` should have done the trick...

---

