---
title: "Scp permission denied"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by andyzammy on 2011-03-20
Hi all,
 I have a net book on which Im running ubuntu server. I've attached a usb hard drive to it, and I successfully added it to fstab with

```
/dev/sdb /media/EXTHD1TB ext3 user 0 0
```

However, I can't seem to copy anything to this place, still getting a permission denied when i try.

If it helps heres the test command I try to copy over with:

```
scp ./scptest user@server:/media/EXTHD1TB
```


Any help with this would be greatly appreciated

---

### Post by SeijiSensei on 2011-03-20
What permissions did you set on the directory /media/EXTHD1TB before mounting the drive?  Does the user in the scp command have write permissions there?  Try this:

```

cd /
sudo umount /media/EXTHD1TB
sudo chown -R user.root /media/EXTHD1TB
sudo chmod 0775 /media/EXTHD1TB
sudo chmod -R ug+rw,o+r /media/EXTHD1TB/*
sudo mount /media/EXTHD1TB

```

where "user" is the one you are connecting as using scp.  Now that user (and the root user) have write permissions.  Everyone else has read.  The -R will change the ownership and permissions on all files below the /media/EXTHD1TB directory.  If that's not what you want, you'll need to change permissions manually.

If you get a "device in use" error when running "umount", you'll need to figure out what programs are accessing the external drive and shut them down first.  Try "sudo lsof | grep /media/EXTHD1TB" to find the processes owning those files.

---

### Post by andyzammy on 2011-03-20
This still gives me a permission denied.. The 2nd chmod command did nothing, the hard drive is new, only having a lost and found folder inside it.

this is ver strange, it didn't need any sort of configuration when I was doing this with my virtual machine server (or is that because it was using a special filesystem?)

Thanks for your help

---

### Post by andyzammy on 2011-03-20
Okay I think i solved the problem.. I did a chown on the mount point whilst the hd was mounted (so that changed ownership of that filesystem), can now scp to that location.

It's still weird though, Im sure I never had to do that in the VM..

---

