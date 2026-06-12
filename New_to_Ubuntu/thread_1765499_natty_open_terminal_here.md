---
title: "natty open terminal here"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-05-23
Hi Everyone,

Is there a way to choose to open the terminal in the folder you are in.  I liked the nautilus script Open Terminal Here and would like to have that feature in 11.04.

---

### Post by mikewhatever on 2011-05-23
Install **nautilus-open-terminal**, logout, login.
...or you may need to reboot.

Edit: Apologies for the typo.

---

### Post by GrouchyGaijin on 2011-05-23
> **mikewhatever said:**
> Install [Bnautilus-open-terminal[/B], logout, login.
...or you may need to reboot.

Will do thanks!

Do you happen to know of any clipboard utilities like parcellite that work with Natty?

I haven't tried it yet but since parcellite runs from the panel I don't think it will work well.

---

### Post by GrouchyGaijin on 2011-05-23
OK I'm slow - where can I find Bnautilus-open-terminal?
I looked in the repos and did a Google search, but couldn't find it.

---

### Post by webofunni on 2011-05-23
There is a option to use classic gnome desktop in new version. That should support clip utilities

---

### Post by collisionystm on 2011-05-23
> **GrouchyGaijin said:**
> OK I'm slow - where can I find Bnautilus-open-terminal?
I looked in the repos and did a Google search, but couldn't find it.

open software center and type

```
nautilus terminal
```

---

### Post by philinux on 2011-05-23
> **GrouchyGaijin said:**
> OK I'm slow - where can I find Bnautilus-open-terminal?
I looked in the repos and did a Google search, but couldn't find it.

No B. Thats was a fail **bold**.

```
sudo apt-get install nautilus-open-terminal
```

Or use synaptic etc etc.

You need to logout then in for it to to be enabled.

---

### Post by GrouchyGaijin on 2011-05-23
```
sudo apt-get install nautilus-open-terminal
```

Or use synaptic etc etc.

You need to logout then in for it to to be enabled.[/QUOTE]

Thanks, now I feel really stupid.  I see that I have it installed.
How do I launch it?

By the way clipit works fine in Natty.

---

### Post by philinux on 2011-05-23
> 
How do I launch it?


It's not exactly how you describe it in your first post. You have to right click on a folder and it's in the list of options.

---

### Post by GrouchyGaijin on 2011-05-23
> **philinux said:**
> It's not exactly how you describe it in your first post. You have to right click on a folder and it's in the list of options.

Thanks man, sorry for being so slow.

---

### Post by philinux on 2011-05-23
> **GrouchyGaijin said:**
> Thanks man, sorry for being so slow.

No worries. Remember there are no stupid questions and there is no spoon!!

---

### Post by webofunni on 2011-05-23
> **philinux said:**
> 
You need to logout then in for it to to be enabled.

I like that application. I guess we can just execute 

```
killall nautilus
```

to enable it. No need to logout/login. 4 sure make sure that u r not using any nautilus related tasks.

---

### Post by GrouchyGaijin on 2011-05-23
Does this work only because 11.04 has the "classic" option?
I noticed that I can still create key combinations to open folder using:

```

nautilus /home/john/Downloads

```

for some reason I thought 11.04 didn't use nautilus.  I wonder if this will work when 11.10 comes out?

Does anyone know if there is a way to use the nautilus scripts in 11.04 (Unity not classic) as well?

---

