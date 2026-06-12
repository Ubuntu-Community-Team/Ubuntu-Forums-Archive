---
title: "md5sum on entire CD?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by minsf on 2009-01-27
this is probably a quick one for you bash gurus :)
how do i check md5sum for a CD image?

i have the hash of the entire .iso file and i want to check that it has been burnt successfully on a CD. my problem: since the image is on the CD itself, bash sees it as "many files on a CD" rather than one .iso file. 
a partial solution would be to export the CD into a .iso file on the HD ([COLOR="Red"]how?[/COLOR]) and run md5sum on it. 
but i would prefer a solution (probably faster) that runs md5sum on the entire CD as it is now ([COLOR="Red"]how?[/COLOR]), rather than spending time on creation of the iso image.

---

### Post by blueridgedog on 2009-01-27
You can export the cd back to the hard drive as an ISO with the following in a terminal:

```
dd if=/dev/scd0 of=/home/username/test.iso
```

(change cdrom0 as needed as well as username and your desired name of the iso)

---

### Post by Sjeti on 2009-01-27
Nevermind, what I was going to suggest didn't work.

---

### Post by caljohnsmith on 2009-01-27
How about doing:
```
sudo dd if=/dev/sdc0 | md5sum
```
You'll need to give the actual device name for the CD drive, not a mounted folder, so you can check first with:
```
mount 
```
And where it shows a line like:
```
/dev/[COLOR="Blue"]scd0[/COLOR] on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=john)
```
That will tell you the CD drive device name to use with the dd command. Let me know how it goes or if you run into problems. :)

---

### Post by stchman on 2009-01-27
> **minsf said:**
> this is probably a quick one for you bash gurus :)
how do i check md5sum for a CD image?

i have the hash of the entire .iso file and i want to check that it has been burnt successfully on a CD. my problem: since the image is on the CD itself, bash sees it as "many files on a CD" rather than one .iso file. 
a partial solution would be to export the CD into a .iso file on the HD ([COLOR="Red"]how?[/COLOR]) and run md5sum on it. 
but i would prefer a solution (probably faster) that runs md5sum on the entire CD as it is now ([COLOR="Red"]how?[/COLOR]), rather than spending time on creation of the iso image.

The md5sum function is not used for checking CD integrity.  But you could try K3b to create and image(.iso) and then md5sum it.

Most users on this forum will feel that is you download and check the md5sum you will get a good burn.  I usually burn my Ubuntu CDs at 16X.

---

### Post by minsf on 2009-01-27
thanks guys.

stchman, even though i dont use k3b/kde, your post sent me in the right direction and i used Applications>Sound>Brasero>Tools>CheckIntegrity to check the CD's md5 against an md5 file that i created from the hash. thanks. that's probably the easiest way to go (though i was looking for a more low level solution like caljohn's and blueridge).

blueridge, i think there is supposed to be a = after the "if", right?

anyways, both caljohn and blueridge resulted in an input/output error from the dd after about 732MB and the md5sum didnt match. this is probably the kind of low level commands i was looking for, so thank you guys and let me know if you have any idea how to fix this error:
```
$ sudo dd if=/dev/scd1 | md5sum
dd: reading `/dev/scd1': Input/output error
1429328+0 records in
1429328+0 records out
731815936 bytes (732 MB) copied, 725.172 s, 1.0 MB/s
59a009dd71ce2ee11408e15743113a6e  -
```
(not the md5 sum that i was expecting... btw, i used /dev/scd1 following the /etc/mtab file and the lshw output)

CALJOHN, you've been posting quality posts on many of my threads- the only thing i can do is to let you know that i've notice this and i appreciate every one of them. thank you so much buddy! i'll pay it forward...

---

### Post by caljohnsmith on 2009-01-27
I just now tried the exact same dd + md5sum command on one of my linux distro CDs just to make sure it works, and it works fine for me; what CD are you using? If it has any kind of copyright protection, that would most likely be the issue, because some copy protection schemes actually use unreadable sectors as part of their technique if I remember correctly (that's why in many cases you can't simply use "dd" to clone a DVD movie for example).

---

### Post by blueridgedog on 2009-01-27
> **minsf said:**
> thanks guys.

blueridge, i think there is supposed to be a = after the "if", right?
[CODE]$ sudo dd if=/dev/scd1 | md5sum


Yes, my typo, and you need the device, not the friendly name, another error, but you figured it out.

---

### Post by minsf on 2009-01-27
> **caljohnsmith said:**
>  ...and it works fine for me; what CD are you using? If it has any kind of copyright protection, that would most likely be the issue... 

i think your method is the right way to go. maybe i get the error due to not enough memory. that is, maybe the dd reads it, stores it in the memory before it sends it to the md5sum, and since i run on a lame 512MB it ends in an error. i thought the swap is large enough, but i will try to write it to the HD first, and then run md5sum- if this works, then it is probably a memory thing. i will let you know if this does not work. by the way, the CD is not write protected

cheers :)

---

### Post by minsf on 2009-01-27
tried it again from a different CD drive. this time writing to home:
```
sudo dd if=/dev/scd0 of=/home/minsf/test.iso[CODE]
i got a similiar i/o error. then i tried to limit the block size (bs=8M) to be sure that it is not a memory thing. no luck (interestingly, in both cases i got stuck around the same point after 205MB)
i checked the logs and found the following:
[CODE]
Jan 27 19:04:13 minsf-laptop kernel: [ 2926.067455] end_request: I/O error, dev sr0, sector 402656
Jan 27 19:04:15 minsf-laptop kernel: [ 2926.067472] Buffer I/O error on device sr0, logical block 100664
Jan 27 19:04:15 minsf-laptop kernel: [ 2926.067480] Buffer I/O error on device sr0, logical block 100665
Jan 27 19:04:15 minsf-laptop kernel: [ 2926.067491] Buffer I/O error on device sr0, logical block 100666

```

---

### Post by caljohnsmith on 2009-01-28
Minsf, it sounds to me like you might simply have a bad CD burn. Do you have any other CDs you could try just to see if they give the same input/output error at the same sector (402656)? That will give you a better idea if it is just that CD or if maybe there is something wrong with your CD drive.

---

### Post by blueridgedog on 2009-01-28
I have gotten errors as you describe when using dd to attempt to copy a DVD that had copy protection and when copying a CD or DVD that had an error.

---

### Post by minsf on 2009-01-30
i tried it on a ubuntu 8.04.2 live cd, so no write protected stuff here :)
i dont think the burn is bad, since Brasero checks the md5 file ok
i tried it on a different cd drive, and different live cd (different distribution), and "dd if=/dev/scd1 of=/home/minsf/test.iso" worked with no errors, but i got a bit more bytes than i expected... one time i got 199610368 (instead of 199661568 ). second time i tried it i got 199548928 bytes. wierd...
any clue?

**EDIT:** i started a new thread about this new problem of the iso images not matching. stated the problem more efficiently. take a look here:
[http://ubuntuforums.org/showthread.php?p=6659083#post6659083](http://ubuntuforums.org/showthread.php?p=6659083#post6659083)
in view of this more precise new thread, i consider the current thread as **SOLVED**

---

