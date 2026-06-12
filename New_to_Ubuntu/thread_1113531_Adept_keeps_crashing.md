---
title: "Adept keeps crashing"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Coolsaber57 on 2009-04-01
hi guys, 

My Adept keeps crashing on me.  I have Kubuntu 8.10 and KDE 4.1.


Is there a way to reinstall that app? I'm a newbie here.

---

### Post by keplerspeed on 2009-04-01
You can install - reinstall applications using synaptic, somewhere in your menus. OR open a terminal window, and enter this command;

```
sudo aptitude reinstall adept
```

this will reinstall adept. This may not be a solution to your problem, but try it. Wont hurt.

---

### Post by Coolsaber57 on 2009-04-01
> **keplerspeed said:**
> You can install - reinstall applications using synaptic, somewhere in your menus. OR open a terminal window, and enter this command;

```
sudo aptitude reinstall adept
```

this will reinstall adept. This may not be a solution to your problem, but try it. Wont hurt.

I tried it, but it says:

E: Type 'http://repository.cairo-dock.org/ubuntu' is not known on line 54 in source list /etc/apt/sources.list
E: Type 'http://repository.cairo-dock.org/ubuntu' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'http://repository.cairo-dock.org/ubuntu' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.


I know that the repository thing is because I was trying to figure out something with cairo dock and put that link in the wrong place.  However, I'm not sure why the other list of sources coudln't be read.

I looked for Synaptic, but I don't think that Kubuntu comes with it preinstalled.  How do I fix this? What other information do you guys need to help me?

thanks in advance!

---

### Post by abn91c on 2009-04-01
> **Coolsaber57 said:**
> I tried it, but it says:

E: Type 'http://repository.cairo-dock.org/ubuntu' is not known on line 54 in source list /etc/apt/sources.list
E: Type 'http://repository.cairo-dock.org/ubuntu' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'http://repository.cairo-dock.org/ubuntu' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.


I know that the repository thing is because I was trying to figure out something with cairo dock and put that link in the wrong place.  However, I'm not sure why the other list of sources coudln't be read.

I looked for Synaptic, but I don't think that Kubuntu comes with it preinstalled.  How do I fix this? What other information do you guys need to help me?

thanks in advance!
take out the cairo repos, you may want to upgrade to kde 4.2 also, its more stable

---

### Post by Coolsaber57 on 2009-04-01
> **abn91c said:**
> take out the cairo repos, you may want to upgrade to kde 4.2 also, its more stable

How do I take those out? I can't even remember where I put them in, lol.

I just tried editing the Sources.list file with the command 'vim sources.list' and tried to delete the line, but when I try to delete the line it says:

Found a swap file by the name "/var/tmp/sources.list.swp"
          owned by: me   dated: Wed Apr  1 22:05:21 2009
         file name: /etc/apt/sources.list
          modified: YES


and gives me two explanations about why this is, saying that a program is using the file.  

However, if ignore this and try to continue, and then delete that line, it prompts me saying that sources.list is read only and to use ! to override.

If I do the ":w!" command to save it, it says "E212: Can't open file for writing"

I'm getting more and more lost here. Help?

---

### Post by cheapie on 2009-04-01
Try using sudo before that command.

---

### Post by Coolsaber57 on 2009-04-01
> **cheapie said:**
> Try using sudo before that command.

That's not an option in the vim editor.

Is there any way to make it NOT read-only?

---

### Post by Coolsaber57 on 2009-04-01
> **Coolsaber57 said:**
> That's not an option in the vim editor.

Is there any way to make it NOT read-only?

Woops, I'm a dummy, I had to run vim with the sudo command.

Ok, I fixed Adept!!!!

Thank you so much guys!

---

