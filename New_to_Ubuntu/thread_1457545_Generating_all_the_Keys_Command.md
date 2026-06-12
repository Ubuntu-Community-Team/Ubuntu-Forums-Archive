---
title: "Generating all the Keys Command"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by held7over on 2010-04-18
Ubuntu 9.10 Gnome

I want to install my sources file on several new Ubuntu installs I am going to be doing. My source file will be a mixture of the standard enabled Ubuntu Repositories, custom Repositories like Mediabuntu, and some PPA Repositories.

Once I have copied my sources.list to /etc/apt/sources.list, is there a command that will automatically generate all the proper keys for the above repositories?

-And if I actually also need to copy my ~/.gnupg file down to the new system, is there a command that will tell pkgmanager where the keys are?

And are there any additional files to be copied over or software packages that must be installed before I can complete this procedure and have a working sources list?   

Thanks!  :)

---

### Post by tgalati4 on 2010-04-18
apt-cache search gpg

Perhaps:

sudo apt-get install gpgkeys

man gpgkeys

---

### Post by Paqman on 2010-04-18
> **held7over said:**
> 
Once I have copied my sources.list to /etc/apt/sources.list, is there a command that will automatically generate all the proper keys for the above repositories?


You could write a script which added the repos and got the keys for you.

In the case of Medibuntu, the following block of code will do the trick:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Many other repos will give you a similar block of code you can copy and paste. Ubuntu PPAs are as simple as:
```
sudo add-apt-repository ppa:<repository-name>
```

Copy all of the code you need for the various sources into a new text file, put:
```
#!/bin/bash
```
on the first line, and make it executable. Voila! Now when you run the script, it will automagically add all your sources.

The next obvious step would be to have it install all your packages, too.

---

### Post by held7over on 2010-04-18
Thanks Paqman. So if I understand you correctly, I would start with copying over a beginning source.list that has the #'s uncommented on the standard Ubuntu selections, which gives me all of those. Then I would sequentially copy all the commmandline code manually given by places like Mediabuntu into my txt file, then use the add-apt-repository command for each of the PPA's?  And I then have a script which will finishing setting up sources for me?

Do I then need to run "sudo apt-get update" or am I already set to go?

And yes, I was planning on copying over a apps list next, and I think I already have that procedure worked out.

I was hoping there would be a way to do a straight copy of these gpgkey files directly onto the new systems and save the time it takes to generate them. But this scripting approach will do the job.

Is there a way to cause the cd with these files and this script to automatically open a terminal and run the script in it when a person inserts the cd in the cdrom?

---

### Post by Paqman on 2010-04-19
> **held7over said:**
> Thanks Paqman. So if I understand you correctly, I would start with copying over a beginning source.list that has the #'s uncommented on the standard Ubuntu selections, which gives me all of those. Then I would sequentially copy all the commmandline code manually given by places like Mediabuntu into my txt file, then use the add-apt-repository command for each of the PPA's?  And I then have a script which will finishing setting up sources for me?


You shouldn't ever have to hack into sources.list manually. That block of code for the Medibuntu repo will add the required entries to the file. Breaking it down:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list

```

This adds the entry to sources.list

```
sudo apt-get --quiet update
```

This updates APT so that it now looks for Medibuntu packages, such as:

```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
``` 

This installs Medibuntu's special authenticaion package. Normally repos use a key instead of a package like this.

```
sudo apt-get --quiet update
```

This updates APT again, and this time the packages will be authenticated, so won't require the --allow-unauthenticated switch used above.

So simply putting the Medibuntu code into the script will do all the work. You don't need to include anything from sources.list.

The only real problem I can see with doing this is that if the entries were already in sources.list, the script would add duplicate entries. You could write the script to cope with this, but that's starting to get a bit complicated. 


```
Do I then need to run "sudo apt-get update" or am I already set to go?
```

Stick it at the end of the script.

> 
And yes, I was planning on copying over a apps list next, and I think I already have that procedure worked out.


That one's really easy. Simply put a line in the script containing all the packages you want:

```
sudo apt-get install <package1> <package2> <package3> 
```

> 
Is there a way to cause the cd with these files and this script to automatically open a terminal and run the script in it when a person inserts the cd in the cdrom?

Not as far as I know, but all you should need to do is point and click on the script.

---

### Post by tgalati4 on 2010-04-19
If you put your script in the root directory of the CD and name it autorun or autorun.sh it might run automatically.  Normally a dialog box pops up asking if you want to run the script.  You need to make the script executable:

sudo chmod +x autorun.sh

If booting from a Live CD, the environment is different since the cdrom is mounted as a root file system and no longer treated as a normal removeable media device.  So I would expect some tweaking to get it to work as you intended.

---

### Post by held7over on 2010-04-20
I have only written a couple of scripts, so I have a stupid question:

I have a lot of sudo's in my script as it is doing different things. (No I haven't tried testing it yet.) Is that the way it should be? 

-or should I eliminate all the sudo's and just start the script with a su at the beginning? 

Or if I just make the script owned by root, won't it ask me for the password when it is clicked on, which would surely seem that it make it run with root powers without the sudo's?

Thanks!

---

### Post by held7over on 2010-04-20
**tgalati4** -- There's a root directory on a cd???! Wow! That sounds interesting. How does one create such a thing?-or where can I read about this? I have only used cds to store data and have gotten used to thinking of them this way only.

---

### Post by Paqman on 2010-04-20
> **held7over said:**
> 
I have a lot of sudo's in my script as it is doing different things. (No I haven't tried testing it yet.) Is that the way it should be? 


That's absolutely fine. You'll only be asked for the password the first time.

---

