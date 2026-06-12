---
title: "Could not update ICEauthority file"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-10-06
I logged in today and I got an interesting error.
```
Could not update ICEauthority file /home/username/.ICEauthority
```
I have no idea why this is happening. I tried looking for an explanation but couldn't really find what that file even does. I found that the permissions might have changed for some reason. So I changed the ownership using chown and then logged out and back in. I still have that problem.

---

### Post by ptn107 on 2009-10-06
```

sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority

```

---

### Post by philinux on 2009-10-06
[https://help.ubuntu.com/community/Troubleshooting#Software%20Issues](https://help.ubuntu.com/community/Troubleshooting#Software%20Issues)

---

### Post by Lampi on 2009-10-06
you should rename the file - xserver will recreate it with the necessary permissions if you try to login afterwards - if it works fine again remove the renamed file

---

### Post by slughappy1 on 2009-10-06
Thanks the chmod seems to have fixed the problem. Can anyone tell me what the file does and why the permissions changed?

---

### Post by rbc on 2009-10-06
[http://ubuntuforums.org/showthread.php?t=206985](http://ubuntuforums.org/showthread.php?t=206985)

---

### Post by slughappy1 on 2009-10-06
Thanks

---

### Post by Red.Dragon on 2009-11-02
This fix does not work for me. 

As soon as I began getting this error message, which I suppose was after I updated my sources, my notifications and sound stopped working. 

I chowned .ICEauthority and yet I still get the same error. 

Any other steps I could take to figure out what is wrong or how to fix this? 

I heard creating a new user fixes this problem, but I have a lot of important data on my user and I want a quick fix.

---

### Post by philinux on 2009-11-02
> **Red.Dragon said:**
> This fix does not work for me. 

As soon as I began getting this error message, which I suppose was after I updated my sources, my notifications and sound stopped working. 

I chowned .ICEauthority and yet I still get the same error. 

Any other steps I could take to figure out what is wrong or how to fix this? 

I heard creating a new user fixes this problem, but I have a lot of important data on my user and I want a quick fix.

See post #3 and link. you have to do exactly what it says in the correct order.

---

### Post by Red.Dragon on 2009-11-02
I already attempted this fix. 

That was the intention of saying "This fix does not work for me." 

I followed all steps posted in Post #3, rebooted, and the error still continues and I checked ownerships of .ICEauthority, even went over the process again, rebooted, and nothing. 

Any other ideas? 
Could there be a way to get Ubuntu to create a new .ICEauthority file for me?

---

### Post by whitethorn on 2009-11-02
Hi, try just moving it to something else then logging in again.

```
mv ~/.ICEauthority ~/.ICEauthority.bak
```

---

### Post by Red.Dragon on 2009-11-02
Nothing. 

As soon as I logged back in and checked: 

```

matthew@Voyager:~$ ls -l ICE*
-rw-r--r-- 1 matthew matthew 3864 2009-11-01 01:15 .ICEauthority.bak

```

---

### Post by tudor117 on 2009-11-02
Try making sure your whole home directory belongs to your user.

---

### Post by Red.Dragon on 2009-11-02
Ah excellent, that's one thing I didn't check. 

Thanks!

---

### Post by Braytonio on 2010-01-22
This happened to me when I (1) installed Karmic with the option "encrypt home folder", then (2) tried to change my password on my default account. This failed, but I could still log in with my original password. Then (3) I added some new software packages, including packages from the KDE.

Now when I log in, all I see in my /home/me folder is a filed called something like Access-Your-Encrypted.Data.desktop. I need the passphrase created during encryption, but of course that is stored in my /home/me/ecryptfs directory. I really did mean to write that down eventually.

A French forum suggested booting up without logging in, creating a new admin user (sudo adduser marcelmarceau admin), then logging in under that new account.

From there, install KDM, which the Frenchies said would provide the .ICEauthority file and voila! I am going to try that. Let you know.

---

### Post by raywood on 2010-10-30
The solution for me was to make sure the home folder belonged to the user.  I've [written up that and other possible solutions]("http://raywoodcockslatest.blogspot.com/2010/10/ubuntu-1010-error-could-not-update.html").

---

### Post by badboy_2083 on 2010-11-02
I had the same issue I changed ownership of the entire home folder to the user. Just changing ownership of the file didn't work for me.

---

### Post by squirlmazzta on 2010-11-11
Is there a way that we can get rid of the threads that didn't solve this problem. This is the only one that looks like it worked. I used it and my box is running great now. I tried the stuff on the other threads and they didn't work.

---

### Post by aoos on 2011-03-07
> **ptn107 said:**
> ```

sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority

```

Hi ,i pasted these commands into my terminal, and i lost  access to  my account! i cannot even login! i get error about nautilus can't access home folder and such! Can you help?:(

---

### Post by mikkellund42 on 2011-03-08
> **ptn107 said:**
> ```

sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority

```

This solved the problem for me. Thanks a lot!

---

### Post by mortasa on 2011-03-30
This happened to me when I install a TV software (veetle.sh) to my system. When I check the ownership for my home folder, I could see ownership has given only for root.

Changing the ownership did work for me and my sound has come back.:popcorn:

Thanks for all.

---

### Post by LanceRooke on 2011-12-10
Mine says '/home/gabe/.ICEauthority' : No such file or directory

---

