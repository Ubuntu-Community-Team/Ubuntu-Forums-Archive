---
title: "Connection time out??"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by juil on 2010-09-30
I just added a medibuntu repo using the sources list generator. I also ran the sudo command as shown below:

```
### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-## get update 
deb http://packages.medibuntu.org/ lucid free non-free 
deb-src http://packages.medibuntu.org/ lucid free non-free 
```

Then when I run 'sudo apt-get update' I get this error:

```
Get:5 http://mirror.csclub.uwaterloo.ca lucid-updates Release.gpg [198B]                                                     
Err http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-updates/main Translation-en_CA                                           
  Could not connect to mirror.csclub.uwaterloo.ca:80 (129.97.134.71). - connect (110: Connection timed out)
```

Also what is this Translation-en_CA??

```
Err http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-security/universe Translation-en_CA
  Unable to connect to mirror.csclub.uwaterloo.ca:http:
```

It seems like these errors happened after these steps. Or is it just a coincidence?

---

### Post by juil on 2010-09-30
bump. This is important. As it seems to be more than a connection problem...

---

### Post by andrewthomas on 2010-10-01
Do you live in Canada?  
 
Open up software sources and select : Main Server  from the drop down menu.
 
Close up and retry command.  
 
Post full error message, if any.

---

### Post by juil on 2010-10-01
Hmm, it worked out fine when i switched to main server. Thank you.
Yes I live in Toronto, and i chose waterloo because it's close to Toronto. But i guess it was a timing out issue after all....

EDIT: I'm trying to understand the relationship between software sources and sources.list. In the screenshot i attached, in the 4th and 3rd last line, you see Medibuntu and Medibuntu (source). That was checked but I didn't see the deb line in the sources.list. I don't understand why.

But when i added the medibuntu line as shown in my first post, it appeared in the software sources as highlighted with the red marker in the screenshot. I don't understand this. Can someone explain this to me?

---

### Post by ankspo71 on 2010-10-01
Hi,
What you see in your software sources list is a cleaned up version of what you would see in your /etc/apt/sources.list file. "deb" and "deb-src" are not really necessary for ordinary users to see in the software sources list, so they are not shown. This is also true for the lines that start with # and ##, which are either to begin a line with a comment/description, or used to disable a repository.

If you would like to see more info on Ubuntu's repositories, here is some documentation that goes into some detail.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you were having the time out error today, it might be because Ubuntu 10.10 (Release Candidate) was just released, and everybody in your area was downloading it from your Ubuntu download server ([http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/)). When the final 10.10 version is released on October 10th, you can usually expect some more of this to happen for a few days.

I have no idea what Translation-en_CA is there for though.

---

### Post by andrewthomas on 2010-10-01
> **juil said:**
> 

EDIT: I'm trying to understand the relationship between software sources and sources.list. In the screenshot i attached, in the 4th and 3rd last line, you see Medibuntu and Medibuntu (source). That was checked but I didn't see the deb line in the sources.list. I don't understand why.


Medibuntu will actually create its own file, medibuntu.list in the /etc/sources.list.d/ directory.

As for the  Translation-en_CA, this is normal, at least for 10.10, as I get a bunch with   Translation-en_US.  They are empty because a translation is not necessary in this case.

---

### Post by juil on 2010-10-01
Thanks for your replies. But I still don't understand why the Medibuntu in the 3rd and 4th last line was showing in Software Sources but not in sources.list. (Please note that this is BEFORE I added the below) I checked the sources.list and i could not find the medibuntu repo. Is this a small minor 'glitch' or is there something i don't understand?

```
### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-## get update 
deb http://packages.medibuntu.org/ lucid free non-free 
deb-src http://packages.medibuntu.org/ lucid free non-free 
```

---

### Post by ankspo71 on 2010-10-01
Hi,
Some applications might add this medibuntu repository for you. I think Ubuntu Tweak might be one of them.

Or did you by any chance run this script to get dvd playback with libdvdcss? /usr/share/doc/libdvdread4/install-css.sh This gets the files needed from medibuntu.

Also andrewthomas pointed out that Medibuntu will actually create its own file, medibuntu.list in the /etc/apt/sources.list.d/ directory. Which is another reason how it would have shown up in your sources list, but not in /etc/apt/sources.list. I forgot to mention the /etc/apt/sources.list.d/ directory in my other reply.

Hope this helps.

---

### Post by andrewthomas on 2010-10-01
> **andrewthomas said:**
> **Medibuntu will actually create its own file, medibuntu.list in the /etc/sources.list.d/ directory.**

.
look in /etc/sources.list.d/ directory

---

### Post by juil on 2010-10-01
Oh, i see. That's understandable. So if it creates the medibuntu file in the sources.list.d directory, it will not show up in the sources.list file.

---

### Post by andrewthomas on 2010-10-01
> **juil said:**
> Oh, i see. That's understandable. So if it creates the medibuntu file in the sources.list.d directory, **it will not show up in the sources.list file**.
Correct.

---

