---
title: "Restoring to default settings"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by cgault9 on 2009-01-14
Hi, I recently got a Sylvannia netbook that came preloaded with ubuntu on it. My roomate got ahold of my computer last night and royally messed something up, I no longer have and minimize, maximize, or close buttons on my windows, I completly lost track of my network settings and the wifi won't connect to any servers, plus the menu bar is now locked, or welded it seems, to the vertical axis of my screen instead or horizantally. 


Can I simply restore my settings to the factory defaults and start over? (ie like a windows system restore point?)

---

### Post by Michael.Godawski on 2009-01-14
hi,

unfortunately there is no such thing as a restore point in Ubuntu.
But...

The panels can be dragged to the position you want them to be.

Check in System > Preferences > Appearance if you can select another theme or if you are using visual effects. If you are using compiz you can add the missing minimize/maximize border by adding windows decoration (dont remember the name exactly) in the ccsm manager.

Regarding the wlan -  can you please post the output of these terminal commands:
```
sudo lshw -C network
iwconfig
sudo iwlist scan
```

---

### Post by mapes12 on 2009-01-14
> **cgault9 said:**
> Can I simply restore my settings to the factory defaults and start over? (ie like a windows system restore point?)No. If everything is screwed up then you will need to reinstall. However, in Ubu this is much easier than in windoze. Backup your /home folder (this contains all your files, firefox bookmarks and personal settings) then once the reinstall is complete then copy across your backed up /home folder to have everything as it was before things went pear shaped.

Alternatively, [move /home to its own partition]("http://ubuntuforums.org/showthread.php?t=46866") and use the **Manual** option when the installer gets to the **Partitioning** section. Just set the variables for each partition.

To make sure you keep all your downloaded updates and applications then back them up as well with Aptoncd. Search for it in Synaptic.

---

### Post by cgault9 on 2009-01-14
only problem is that since it is a netbook there are no CD drives... 
this will really suck without being able to restore defaults haha

---

### Post by mapes12 on 2009-01-14
> **cgault9 said:**
> only problem is that since it is a netbook there are no CD drives... 
this will really suck without being able to restore defaults hahaYou should read your machines [documentation]("http://www.sylvaniacomputers.com/documentation.php") before asking forum members to do it for you.

---

### Post by Montblanc_Kupo on 2009-01-14
Seems like if things are just screwed up in the account, you could create a new user account on the machine and move the /home folder into it... then just delete the old user account.

---

### Post by cgault9 on 2009-01-14
> **mapes12 said:**
> You should read your machines [documentation]("http://www.sylvaniacomputers.com/documentation.php") before asking forum members to do it for you.

I read my documentation... never asked you too.
thanks for the link and the scolding though i guess.


I am looking for a terminal sudo code or something along those lines that will wipe anything I may have installed or set-up and give me a blank slate: if i simply need to reformat I'll look around the forum for ways to do that on the netbook. thnx..

---

### Post by cgault9 on 2009-01-14
> **Montblanc_Kupo said:**
> Seems like if things are just screwed up in the account, you could create a new user account on the machine and move the /home folder into it... then just delete the old user account.

good idea, thank you. Can I make a second account with administrative allowances as well?

---

### Post by ubrox on 2009-01-14
Yes you can! this is the best coure of action. No need for a reinstall. Create a new user as follows:
System->Administration->Users and groups
Add User
Provide the needed info
In the "User Privileges" tab, check the "Administer the System" box in addition to anything else you want.

That is it. Login as the new user. 

It is also possible to recover your existing account, but that may need lot more hand holding for you. 

Now .. creating a new user may not necessarily solve your wireless issues depending on what got messed up. But we can get to that later. 

Yeah. that guy was mean to you for some reason. But its ok .. this forum is one of the most friendliest and most useful one on the web. Dont let one post dishearten you.

---

### Post by cgault9 on 2009-01-14
> **kalyanakrishna said:**
> Yes you can! this is the best coure of action. No need for a reinstall. Create a new user as follows:
System->Administration->Users and groups
Add User
Provide the needed info
In the "User Privileges" tab, check the "Administer the System" box in addition to anything else you want.

That is it. Login as the new user. 

It is also possible to recover your existing account, but that may need lot more hand holding for you. 

Now .. creating a new user may not necessarily solve your wireless issues depending on what got messed up. But we can get to that later. 

Yeah. that guy was mean to you for some reason. But its ok .. this forum is one of the most friendliest and most useful one on the web. Dont let one post dishearten you.

thanks, after about 3 more hours of fiddling around i got it to work finally...
thanks again all.

---

### Post by ubrox on 2009-01-14
I am glad it is solved. If you have not done so already, please mark this thread as solved using "thread tools"

---

