---
title: "help"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by mamawiggles on 2009-09-24
Ok here goes, I have a good friend who had a computer equipped with Windows and her son decided that she should have linux OS instead.  So, she can no longer find her Outlook Express emails or any of the original games that she used to enjoy including plain ole solitare.  He supposedly imported her address book but she has no clue how to find it.  I am sure her son meant well but this is a mess.  Can someone please explain in simple plain english, how she can get this to work???  Thanks in advance.

---

### Post by potat on 2009-09-24
Is there any more information you can tell us? For example, did her son set up a dual-boot system (meaning Windows is still installed side-by-side with Linux)?

---

### Post by unmole on 2009-09-24
I don't mean to be an *** but it would really help if your post's title was a little more descriptive than just help.

---

### Post by Elfy on 2009-09-24
Can you either do it yourslef or get your friend to run the following command from a terminal, that is in Apps > Accessories - it will also need the normal password which will  be invisible.

```
sudo fdisk -l
```

---

### Post by ikitson on 2009-09-24
If he format the drive completely then i don't see how she can have all of those with linux at the moment.

---

### Post by gdonwallace on 2009-09-24
The answer is going to depend on how he installed Ubuntu.  

If he did dual boot, meaning that she can no choose either windows or Ubuntu, then she still has access to everything she did before.  She just has to choose to enter Windows when the computer starts up.

On the other hand, if he did a complete install of Ubuntu, then he wiped the hard drive and installed Ubuntu over everything.  Windows no longer exists on that computer.  If that is the case, Ubuntu has some of the same games that windows does, just a different menu structure; but she will find them.  They are located on the menu Applications --> games.  As to outlook express, that is gone.  If she did not do a online backup of her address book, that will be gone as well....sorry for the bad news on that.  However; there are programs that will work in Ubuntu that will give her the functionality of Outlook Express.  (My recommendation is Mozilla Thunderbird.  

Let us know how the install was done, and we can get into more detail after that.

---

### Post by doas777 on 2009-09-24
well, the default email client for ubuntu is Evolution, available from the default shortcut on the top panel (the one that looks like an envelope) or from Applications -> Internet -> Evolution

if the son imported the address book, then it should be in evolution.

as for games, check under Applications -> Games. there are several kinds of solitare available.

poke around the Applications menu and you will find most of what you have mentioned.

the email MAY also be recoverable depending on how the mail server and outlook express were set up. if the mail is still on the server, all you have to do is configure evolution to check that account, and it will pull down all the message it does not already have (which would be all of them). if the mail is not saved on the server then there is likely little that can be done, unless the box is a dual boot, or the son backed up the email.

just out of curisoity, why isn't the son answering these questions? not that we mind, just curious.

---

### Post by LewRockwell on 2009-09-24
> **mamawiggles said:**
> Ok here goes, I have a good friend who had a computer equipped with Windows and her son decided that she should have linux OS instead.  So, she can no longer find her Outlook Express emails or any of the original games that she used to enjoy including plain ole solitare.  He supposedly imported her address book but she has no clue how to find it.  I am sure her son meant well but this is a mess.  Can someone please explain in simple plain english, how she can get this to work???  Thanks in advance.

which *nix

.

---

### Post by doas777 on 2009-09-24
I think we have all just fallen for one of those linsux trolls.

---

