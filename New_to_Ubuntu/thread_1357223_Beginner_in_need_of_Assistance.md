---
title: "Beginner in need of Assistance"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Yoaly on 2009-12-17
Several hours ago I replaced Windows Vista with Ubuntu Karmic (9.10) i386. The installation process went smoothly, it is signing the Code of Conduct that is giving me problems. I have downloaded the file and have it on my desktop; when entering the command "gpg --clearsign UbuntuCodeofConduct-1.1.txt," as stated in the instructions, all that I see is 

gpg: can't open `UbuntuCodeofConduct-1.1.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.1.txt: clearsign failed: file open error

I also tried to  copy and paste the command from the website to the terminal, the result was displaying the Code of Conduct in the terminal.
So far, variations of the command I tried have yielded the first result or other failures. The .asc file is not made, as a consequence I cannot sign the Code of Conduct.

Help would be greatly appreciated as I have no idea as to what I'm doing. My knowledge of how Ubuntu works is equivalent to that of a infant working with a computer for the first time. Thank you for you assistance and your time.

---

### Post by CharlesA on 2009-12-17
Can run these commands and post the results?

```
pwd
ls -l

```

---

### Post by northern lights on 2009-12-17
As you've downloaded the file to your desktop, the command\s got to point there as well.

Either:
1. move the file to /home/user/ (where user is your username)

2. run```
gpg --clearsign ~/Desktop/UbuntuCodeofConduct-1.1.txt
```3. run```
cd ~/Desktop
gpg --clearsign UbuntuCodeofConduct-1.1.txt
```

---

### Post by Yoaly on 2009-12-17
> **CharlesA said:**
> Can run these commands and post the results?

```
pwd
ls -l

```

This is what comes up.

yoaly@yoaly-laptop:~/Desktop$ pwd
/home/yoaly/Desktop
yoaly@yoaly-laptop:~/Desktop$ ls -l

---

### Post by llawwehttam on 2009-12-17
Oh i've been using ubuntu for 2 years now and i've never heard of the code of conduct. What is it?

---

### Post by llawwehttam on 2009-12-17
OK, just had a look at it but i've never seen it before. Do you have to sign it?

---

### Post by cenzorrll on 2009-12-17
as far as i know the code of conduct only need to be signed by people who represent ubuntu, such as forum moderators.  not the end user.

---

### Post by northern lights on 2009-12-17
> **llawwehttam said:**
> Oh i've been using ubuntu for 2 years now and i've never heard of the code of conduct. What is it?[http://www.google.com/search?q=ubuntu+coc]("http://www.google.com/search?q=ubuntu+coc")

---

### Post by Yoaly on 2009-12-17
Thank you for your help, it worked splendidly.

---

### Post by isa.dsouza on 2012-09-19
This helped. But still had a load of trouble signing the code of  conduct. Encryted file was a problem so I installed Thunderbird and  enigmail addon to decrypt the email link that gets sent to activate the  PGP for Launchpad. 

Now I have some other issues to sort out. Hopefully I should sort them  out. Bottomline is I have signed the code of conduct finally. Other  matters now regarding the Passphrase & Keyrings etc need to be  sorted.

Your commands helped in converting the code of conduct to the .asc extension. Thank you again.

---

### Post by grahammechanical on 2012-09-19
The Ubuntu Code of Conduct is the basis for governing the behaviour of forum members. We do not have to sign the Code of Conduct in order to participate in the forums. We are expected to follow it when posting on the forum.

If we want to get more involved in the Ubuntu Community then signing the code of conduct may be a requirement for involvement. For example, a signed Code of Conduct is necessary for joining any of the official Ubuntu teams.

I found this screen cast useful:

[http://screencasts.ubuntu.com/2010/12/22/004-SigningCoC]("http://screencasts.ubuntu.com/2010/12/22/004-SigningCoC")

Regards.

---

