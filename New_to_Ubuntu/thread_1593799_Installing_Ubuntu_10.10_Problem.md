---
title: "Installing Ubuntu 10.10 Problem"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by WickyTicky on 2010-10-11
Right now I am installing Ubuntu 10.10 on to a brand new 80gb SATA hard drive from a CD. Everything goes fine until I reach the point in the installing process where it asks me "Who Are you?" and it asks me my name, the machines name, tells me to pick a user name and password.

The moment this screen pops up, the "Forward" button is unable to be selected. I assume this has to do with the orange loading bar at the bottom so I wait patiently. The orange bar gets to (what looks like) 80% or 85% full when it stops, the CD drive stops spinning (it gets really quiet), and the words above the orange bar read "Ready when you are...". 

The "Forward" button and the "Skip" button are unable to be selected. I'm clueless as to what to do or what is happening.

Some more information I can give you is when I click the side arrow, changing it to a down arrow, the script reads "Oct 11 22:59:15 ubuntu ubiquity[2805]: debconffilter_done: ubiquity.components.install (current: ubi-usersetup)"

Could anyone assist me?

---

### Post by sheldonjace on 2010-10-12
I too am having the same error. I believe it has some relevance to not being able to partition the HD in my case though. I just don't know how to resolve that being as I just used Gparted to create the partitions myself.

---

### Post by Perun84 on 2010-10-12
Exactly the same thing happened to me too now. Did you guys find a solution?

---

### Post by arubislander on 2010-10-12
I'm downloading the 10.10 iso image to install in a virtual machine to get a better feel as to what you mean...

---

### Post by Perun84 on 2010-10-12
I hit the "Back" button to see if I could do anything, but it only took me back to the time and keyboard settings, and when I went forward again, it got stuck with the "Getting the time from a network time server" message and the orange bar set way back. So the "Ready when you are..." message isn't there anymore, but its not doing anything else either. This is what it looks like for me now:

[IMG]http://i315.photobucket.com/albums/ll464/Perun666/Bildschirmfoto-2.png[/IMG]

---

### Post by philinux on 2010-10-12
Just a thought.

Try the "require password to login" option. You can set it to auto login after install.

---

### Post by Perun84 on 2010-10-12
Does nothing. :(

---

### Post by drdos2006 on 2010-10-12
I have just installed the desktop 32bit version in a second partition where the first partition was server 10.10 32bit. I did not see the problems you are having. I had downloaded via BitTorrent and verified before burning to CD. I used the desktop version of gparted to reduce the size of the server partition before installing the desktop version. I booted into the testing version to use gparted before then installing, if that helps. 

Maybe do a md5 checksum to see if the iso has downloaded properly.  Installed on a P4 3.00 ghz Intel with ASUS motherboard, 2 gig RAM.

regards

---

### Post by arubislander on 2010-10-12
I see your username starts with a Capital Letter. Usernames should be all in lowercase in Linux. You'll also have noticed there's no green checkmark behind the username entry field.

---

### Post by Perun84 on 2010-10-12
What do you know... Now I feel sheepish. Really, sheepish.

---

### Post by arubislander on 2010-10-12
You shouldn't. It's not as clearly indicated as it was in the past. How were you to know?

---

### Post by ft-Orchard on 2010-10-12
> **arubislander said:**
> I see your username starts with a Capital Letter. Usernames should be all in lowercase in Linux. You'll also have noticed there's no green checkmark behind the username entry field.

Should this not be fixed in the Ubuntu installer? If it must be all lowercase, there should be a warning.

---

### Post by arubislander on 2010-10-12
I agree. It used to be clearly mentioned, but this new installer is very terse...

---

### Post by ashwinhgtx on 2010-10-12
> **Perun84 said:**
> What do you know... Now I feel sheepish. Really, sheepish.

Did you manage to complete the installation?

---

### Post by konang on 2010-10-13
I have the same problem here, does anyone have a real answer?

---

### Post by arubislander on 2010-10-14
Why not post a print-screen of your situation? Perun84 got his system up and running after correcting his username.

---

### Post by Danmarale on 2010-10-18
Thank you [Arubislander]("http://ubuntu-ky.ubuntuforums.org/member.php?u=375602").  The use of a capital letter in the user name I chose had stalled my installation at the "Who are you?" stage.  Thanks a lot!!!

---

### Post by aqk on 2010-12-26
AAAIIIIEEE!   Oops!  Sorry for the upper-case...!

I had previously installed Ubu 10.10 on another laptop- no problem.

I finally got around to installing the same CD over xmas holidays on an old Celeron laptop that was still running (ugh) Vista (in a dual partn).
Try as I might, it would not active the "forward button!"
So after a couple of hours of cursing, I finally went to the internet and found this thread.
 LOWER-CASE!
But my user name (UC) had a big checkmark beside it, indicating it was OK! 
  Once I switched it to lc, the install continued normally 
Thanx, above guys!

mr. shuttleworth, kick this install designer guy in the lower-case!

---

### Post by Vi3tHoneyX on 2010-12-27
[COLOR="DarkRed"]Ha, it's funny to see that so many people had the same problem as me! Now I don't feel so bad and can stalk the forums to help others with this same problem.[/COLOR] xD

---

### Post by IWantFroyo on 2010-12-27
The name of the computer CAN'T BEGIN OR END IN A _CAPITAL_

---

### Post by raonyguimaraes on 2011-03-31
Dude, I was having the same problem why the f*** the installer is not checking if there is a capital letter in there?

---

### Post by pjorge1036 on 2011-03-31
> **arubislander said:**
> I see your username starts with a Capital Letter. Usernames should be all in lowercase in Linux. You'll also have noticed there's no green checkmark behind the username entry field.
WOW now I feel really STUPID!

Thanks!

---

