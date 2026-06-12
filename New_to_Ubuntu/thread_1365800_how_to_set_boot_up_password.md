---
title: "how to set boot up password"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mickeyjoe on 2009-12-27
2 quick questions

a)  how do i set Ubuntu to ask for an administrator password upon boot after i selected for it not to ask for one upon installation

b) how do i set the Bios to have a password upon bootup instantly

---

### Post by KaitLynnHt on 2009-12-27
I think I found an answer for 'a'.  I found this in the forums --> [http://ubuntuforums.org/showthread.php?t=1123459](http://ubuntuforums.org/showthread.php?t=1123459)<-- I can't test it since I'm using lxde so my option are different and all greyed out.

I'm clueless about BIOS stuff... sorry...

---

### Post by mickeyjoe on 2009-12-27
ok thanks, and a follow up question:  How can I change my administrator password.

---

### Post by David Delony on 2009-12-27
If you're already an administrator, I believe you can just change your regular password.

---

### Post by mickeyjoe on 2009-12-28
> **David Delony said:**
> If you're already an administrator, I believe you can just change your regular password.

That's what I need to know how to do.

---

### Post by mörgæs on 2009-12-28
Have you read this about the root account?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mickeyjoe on 2009-12-28
> **mörgæs said:**
> Have you read this about the root account?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I read over that, but unless I'm missing something, I didn't see where I can change the password for my main [root] account [administrator level user] - ?

I don't have a problem doing it with a sudo in terminal, just need to know how to.

?

---

### Post by mörgæs on 2009-12-28
In general it is not recommended to use the root user at all. I know root is used in other distros, but in Ubuntu the prefered way is using the normal user, just taking full rights with sudo when needed.

In other words: If you have not found out how to change password for root, be happy about this :-)

---

### Post by mickeyjoe on 2009-12-28
> **mörgæs said:**
> In general it is not recommended to use the root user at all. I know root is used in other distros, but in Ubuntu the prefered way is using the normal user, just taking full rights with sudo when needed.

In other words: If you have not found out how to change password for root, be happy about this :-)

I just want to do the following:  Upon installation of Ubuntu I gave my system a password [like when I install software I have to type this password in or upon boot].  I want to change "that" password.  How do I change "that" password?

---

### Post by mbzn on 2009-12-28
For the root password, if you mean the password you have to enter after sudo or when requiring admin privileges(this is your own password if you are the owner of the pc/the first user at installation) you can use the passwd command in console.

The bios you would have to look at the security page, the two options you'd need to look for is "bios password" or something likewise and security level(or likewise) to make the password at boot(not 'when entering setup')

Hope this will help you

PS. you can set-up a password for the bootloader with the app Startup-manager(this works with grub, not sure about grub2)

---

### Post by mickeyjoe on 2009-12-28
> **mbzn said:**
> For the root password, if you mean the password you have to enter after sudo or when requiring admin privileges(this is your own password if you are the owner of the pc/the first user at installation) you can use the passwd command in console.

The bios you would have to look at the security page, the two options you'd need to look for is "bios password" or something likewise and security level(or likewise) to make the password at boot(not 'when entering setup')

Hope this will help you

PS. you can set-up a password for the bootloader with the app Startup-manager(this works with grub, not sure about grub2)

lol - i kinda need baby steps, kinda tell me what to click [or to type into terminal] to get the job done.

---

### Post by mbzn on 2009-12-28
In the terminal: Type

passwd 
Then press enter.

For the bios you need to press either F2 or delete seconds after power-on
Then look around for the things i mentioned.

Go to Aplications>Add/Remove and look for StartUp-Manager for the grub password

---

