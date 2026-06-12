---
title: "roll back gimp"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by trucker33377 on 2011-04-01
Hi I've been using Gimp2.6 for some time now. A while back I found Gimp 2.7.3 and thought I would give it a look. At first everything worked great and I do like it alot. But about a week or so back I think some thing were changed in Gimp on an update. Now it opens fine but I can't do anything with it.So I need to roll it back to the stable 2.6. Can someone tell me how to get 2.6? apt-get keeps putting the 2.7.3 back in.
Thanks

---

### Post by Enigmapond on 2011-04-01
In Synaptic under the "Packages" tab you can force the version you are needing to install. I would purge what you have now and try that.

---

### Post by Phil D. on 2011-04-01
If installed via a ppa, ppa-purge is the way to go.
Install via synaptic or 'sudo apt-get install ppa-purge'
'ppa-purge -h' to see how to use it, you have to know where you updated gimp from.

---

### Post by trucker33377 on 2011-04-01
ive missed something here there is no gimp 2.6.11 to install in the package manager its been replaced with the 2.7.3 . Im not sure how to purge the 2.7.3

---

### Post by beew on 2011-04-01
> **trucker33377 said:**
> ive missed something here there is no gimp 2.6.11 to install in the package manager its been replaced with the 2.7.3 . Im not sure how to purge the 2.7.3

The package manager shows the most updated version in your repositories and it is 2.7.3. But if you right click "gimp" in Synaptic and choose "properties" it has a tab to show all versions available to you.

As others said, use ppa purge to remove the ppa and it will automatically downgrade all the packages installed from the ppa to the next highest version in your repositories. There is no need to force version if you purge the ppa,_you force a version only when you want to keep the ppa but don't want the latest version_

Alternatively, you can use Ubuntu Tweak to purge the ppa.

---

### Post by trucker33377 on 2011-04-01
that didnt work still places 2.7.3
force ver shows 2.6 but it didnt install

---

### Post by beew on 2011-04-01
> **trucker33377 said:**
> that didnt work still places 2.7.3
force ver shows 2.6 but it didnt install

If you purge the ppa you don't need to force version. It would downgrade automatically.

**Edited:**Instructions to purge ppa.
[http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/]("http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/")

---

### Post by trucker33377 on 2011-04-01
sudo ppa-purge gimp 
this dont work using gimp 2.7.3 blah blah dont purge it.
I'm not real good with term.

---

### Post by Phil D. on 2011-04-01
Shoot in the dark,
sudo ppa-purge ppa:matthaeus123/mrw-gimp-svn
the command would look like this.

An option with a GUI is [Ubuntu-Tweak]("http://ubuntu-tweak.com/"). Under 'Packager Cleaner' (select Purge PPAs and Unlock at the bottom to select the PPA)

---

### Post by beew on 2011-04-01
> **trucker33377 said:**
> sudo ppa-purge gimp 
this dont work using gimp 2.7.3 blah blah dont purge it.
I'm not real good with term.

You have to use the ppa instead of the package in the command. 
so it is ```
sudo ppa-purge ppa:matthaeus123/mrw-gimp-svn
```

Check the ppa's line, I cut and pasted from Phil D's post so I am not sure if it is correct.

---

### Post by beew on 2011-04-01
> **Phil D. said:**
> Shoot in the dark,
sudo apt-get purge ppa:matthaeus123/mrw-gimp-svn
the command would look like this.

An option with a GUI is [Ubuntu-Tweak]("http://ubuntu-tweak.com/"). Under 'Packager Cleaner' (select Purge PPAs and Unlock at the bottom to select the PPA)

That command is incorrect, "sudo apt-get purge" remove a package and its configuration files (so the parameter should be the package name. ```
sudo apt-get purge gimp
``` would be correct but it is not what OP wants to do.

OP can also do ```
sudo apt-get autoremove gimp
``` Then remove the gimp2.7 ppa from his sources list and reinstall gimp.

---

### Post by jmszr on 2011-04-01
trucker33377,

You can get a .deb of Gimp 2.6.11 here at GetDeb.net : [http://www.getdeb.net/app/gimp](http://www.getdeb.net/app/gimp) .

---

### Post by beew on 2011-04-02
> **jmszr said:**
> trucker33377,

You can get a .deb of Gimp 2.6.11 here at GetDeb.net : [http://www.getdeb.net/app/gimp](http://www.getdeb.net/app/gimp) .
Why get a .deb when you can add a ppa? :)

[https://launchpad.net/~ferramroberto/+archive/gimp]("https://launchpad.net/~ferramroberto/+archive/gimp")

---

### Post by jmszr on 2011-04-02
@beew,

Actually, it does install it from a ppa. This just seems even simpler than adding a ppa (to me, anyway).

---

### Post by beew on 2011-04-02
> **jmszr said:**
> @beew,

Actually, it does install it from a ppa. This just seems even simpler than adding a ppa (to me, anyway).

With PPA you get updates whereas if you install from a .deb it is static.

---

### Post by jmszr on 2011-04-02
@beew,

Good point.

---

### Post by trucker33377 on 2011-04-02
Hay this worked Gimp downgraded to 2.6.... To bad it didn't fix my problem. I was sure it was the new version of gimp but Its not. Guess I will search again.

---

### Post by trucker33377 on 2011-04-02
Problem solved :) Turns out to be a setting on my Wacom Tablet. My grand daughter loves to use it with gimp 9yrs old. she messed it up. But this was still a good lesson for me. Thanks for the help.
FYI. I think I will wait for Gimp 2.8 to be released. Its going to be a real winner from what Ive seen so far.

---

