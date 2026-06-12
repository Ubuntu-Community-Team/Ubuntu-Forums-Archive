---
title: "Reset User Settings"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by JCollierDavis on 2010-04-23
Just finished installing 10.04 RC on my laptop.  
 
When I installed 9.10 6 months ago, I 
set up an ext4 10gb partition for the root directory and a seperate ext3 120gb for /home.
When I installed, all my old desktop settings, (toolbars, etc) remain as they were before.
 
How do I remove or overwrite these settings so that my new OS will appear as it would be "out of the box" and not essentially look the same as the old one?

---

### Post by arrrghhh on 2010-04-23
> **JCollierDavis said:**
> Just finished installing 10.04 RC on my laptop.  
 
When I installed 9.10 6 months ago, I 
set up an ext4 10gb partition for the root directory and a seperate ext3 120gb for /home.
When I installed, all my old desktop settings, (toolbars, etc) remain as they were before.
 
How do I remove or overwrite these settings so that my new OS will appear as it would be "out of the box" and not essentially look the same as the old one?

Well, the best way would be to start with a fresh /home... but I'm assuming you've already thought of that, and that's why you're posting here... you want to avoid that.

I could recommend a slew of files to rename to see if it would get you back to default, but it'll be a frustrating shot in the dark, and you could end up damaging the system.  You could create a new user, maybe that would be easiest?

---

### Post by iponeverything on 2010-04-23
```

cd /home/
sudo mv user-account user-account.old
sudo cp -a /etc/skel user-account
sudo chown -R user-account.user-account user-account

```

where user-account is the account that you want to reset.

to put the old back in place, move the new one to a new name and move old one back to the original name.

---

### Post by arrrghhh on 2010-04-23
Learn something new every day... didn't think it would be that easy, thanks!

---

### Post by sisco311 on 2010-04-23
never mind

---

### Post by iponeverything on 2010-04-23
> **sisco311 said:**
> Hmmm, almost :)



your third,fifth and sixth steps are combined in this one.
```
sudo cp -a /etc/skel user-account

```

---

### Post by sisco311 on 2010-04-23
> **iponeverything said:**
> your third,fifth and sixth steps are combined in this one.
```
sudo cp -a /etc/skel user-account

```

d'oh, you're right. :redface:

---

### Post by JCollierDavis on 2010-04-23
> **iponeverything said:**
> your third,fifth and sixth steps are combined in this one.
```
sudo cp -a /etc/skel user-account

```
 
Here's what I did that worked perfectly:
NOTE Erasing all my personal settings was exactly what I was after.
I didn't have a /etc/skel directory, but just leaving that command out of the thing it worked exactly as I wanted.
 
thanks
 
 
 
[COLOR=black][FONT=Verdana]To create a new empty home directory, log out, press Ctrl+Alt+F1 to switch to a virtual console and log in.

NOTE: you will lose all your personal settings. 

run:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]cd /home[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]backup the old home:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo mv username username_old[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]create the new one:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo mkdir username[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]set the correct ownership:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo chown -R $USER: /home/username[/FONT][/COLOR]

[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]##This part wasn’t necessary ##[/FONT][/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]copy the default config files to the new home:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]cp /etc/skel/* /home/username[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]cp /etc/skel/.[0-9a-zA-Z]* /home/username[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]
press Ctrl+Alt+F7 (or F8) to go back to the GUI login screen, log in, open a file manager and copy your files (documents, music...) from the old home to the new one.[/FONT][/COLOR]

---

