---
title: "Dell Optiplex GX110 password"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by GoBrandiRanger on 2010-07-17
Ok, I know this isn't exactly an Ubuntu question, but I'm completely new to this and trying my hardest to do this without calling my cousin. 

I bought a Dell Optiplex GX110 a few months ago and it already came with Ubuntu 9.[something]. I desperately need to update it, but I don't have a password. My cousin had it but lost the paper he'd written it down on, so I'm kinda screwed.  

I read somewhere that I can take the PSWD jumper on the motherboard out and that will reset it, but will that do anything to my computer? Delete files or anything like that? I'm not at all computer savvy, so I turn to you.  

Please help me.  
 ~Brandi~

---

### Post by Windows Nerd on 2010-07-17
When you are talking about resetting the PSWD jumper (the correct term is the CMOS jumper, I believe, correct me forum if I am wrong) you are talking about resetting the BIOS password. It does not affect any OS (operating system) passwords. 

Just to be clear, you mean the password you recieve when you are prompted to upgrade the system from 9.X?

Scott

---

### Post by GoBrandiRanger on 2010-07-17
You're probably right about the terminology. As I said, I'm a total noob. lol. I just went by what they called it on another forum.

  And yes, I keep getting the "Update Manager" window every time I turn the computer on. I've tried to update it, but it always asks me for a password, which I don't have. =/

---

### Post by Windows Nerd on 2010-07-17
So it is your user password.

You enter in for that password Update Manager Prompts your for the same one you use to login (unless you have enabled automatic login and don't have to type in your Username and Password to login. You have to use your Username and password to login by default, so you would have had to purposely change it, which requires knowing that password in the first place).

---

### Post by GoBrandiRanger on 2010-07-17
It automatically logs in when I boot it up. I've never had to use a password. It's also still in his name because I don't know how to switch it to mine/don't have the password to do so.

---

### Post by Windows Nerd on 2010-07-17
> **GoBrandiRanger said:**
> It automatically logs in when I boot it up. I've never had to use a password. It's also still in his name because I don't know how to switch it to mine/don't have the password to do so.
Okay, so you don't know your password. You have therefore NEVER updated the computer since you got it, or changed most of the settings (because they require password access)

You want to upgrade Ubuntu to the latest version.

Could you tell me what version you have now?

Run this in terminal:

```
cat /etc/issue
```Scott

---

### Post by _Mark_ on 2010-07-17
> **GoBrandiRanger said:**
>   

I read somewhere that I can take the PSWD jumper on the motherboard out and that will reset it, but will that do anything to my computer? Delete files or anything like that? I'm not at all computer savvy, so I turn to you.  

Please help me.  
 ~Brandi~

The PSWD jumper on the motherboard will only get rid of the BIOS password so you can go in and change the configuration, it won't do anything to the OS at all.

Have done this more than a few times on GX models

---

### Post by GoBrandiRanger on 2010-07-17
I know you'll probably laugh at me, but where can I find said terminal to run the code? >.> And I have no idea which version I have.

---

### Post by Windows Nerd on 2010-07-17
> **GoBrandiRanger said:**
> I know you'll probably laugh at me, but where can I find said terminal to run the code? >.> And I have no idea which version I have.
Gnome Menu>Accessories>Terminal

---

### Post by GoBrandiRanger on 2010-07-17
9.04

---

### Post by Windows Nerd on 2010-07-17
Ok, so if you hit the upgrade button, you will upgrade to 9.10, which is not the latest version either.Just letting you know.

Anyways, you want to find your lost password:

There is an exellent guide written by another forum user:

[http://ubuntuforums.org/showthread.php?t=133102&highlight=forgotten+password](http://ubuntuforums.org/showthread.php?t=133102&highlight=forgotten+password)

Make sure you remember you password now.

Scott

---

### Post by GoBrandiRanger on 2010-07-18
Thank you! My computer is finally updated! It took forever, but it was worth it. It runs a lot smoother now. I couldn't have done it without you.

---

