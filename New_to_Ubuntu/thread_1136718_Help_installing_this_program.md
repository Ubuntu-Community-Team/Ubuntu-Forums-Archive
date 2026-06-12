---
title: "Help installing this program?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by dragonwarriorfan on 2009-04-25
Glad to find this reference. I am a new convert to ubuntu and love it (Jaunty 9.04 on my dell mini 9) - super beginner, though. Can someone help me with the commands to install this program [README]("ftp://petrus.thomasaquinas.edu/pub/linux/words/README")? I'd like to install it and create a link to my favorites. I can extract the file no problem (after reading other posts), but can't seem to get it to run. I expect I won't be able to move the icon for it to favorites, either. Thanks for the help!

---

### Post by sahabcse on 2009-04-25
Hi

click [here]("http://sahabm.blogspot.com/2009/04/ubuntu-package-installation-from-source.html") for Source package installation details

---

### Post by Sidewinder1 on 2009-04-25
Hi Dragon and WELCOME!
I clicked on your 'readme' link and apparently my Firefox doesn't know how to handle the 'FTP' server. Could you copy and paste, into your next post, exactly what you're trying to install?
Thanx

---

### Post by t0p on 2009-04-25
I also cannot access the file in question - the error message Firefox gives me says:

```
Connection Interrupted

The document contains no data.

The network link was interrupted while negotiating a connection. Please try again.
```

So I don't know what this file is.  But anyway, README files are usually text files that the app author puts in the source directory to tell users instructions for installation, TODO lists, bugs and workarounds etc.  I've never heard of an app called README.

---

### Post by glotz on 2009-04-25
There really is no install, only extract it and run it. Open a terminal. Change to the directory where you extracted it. Input ./words

(I didn't actually try it, that's just what the README said.)

If it runs, we can make an icon to launch it.

---

### Post by dragonwarriorfan on 2009-04-25
Sorry, here is a link to the page. I was linking the README so you all might be able to decipher where I can't seem to understand it. Here is the actual link:
[http://users.erols.com/whitaker/wordslux.htm](http://users.erols.com/whitaker/wordslux.htm)

I was able to extract and get an icon on my desktop, but can't get it to run. Some of you suggested running from terminal. If I put in it in the general file system (the extracted file), what would the command be? Can I not just click the icon and open. Again, sorry for the very newbie questions. Thanks for the help in advance. You are a very welcoming community!

EDIT - I can get it to run now by clicking on one of the extracted files and run in terminal. I'd like to move it to favorites, where can I put it to access from there?

---

### Post by glotz on 2009-04-26
What is this *favorites* you speak of?

---

### Post by Sidewinder1 on 2009-04-26
Dragon, I checked the repositories (in 8.04 Hardy Heron, the version that I'm running) in Synaptic Package Manager, and "Words" was not there. Therefore you had no other choice than to  manually download then manually install, which obviously you did successfully. Congrats.
In the future, when you find software or programs, first look for them in Synaptic Package Manager. If it's there, you're only 3 clicks away from using it. You also have the further advantages of (also through Synaptic)  cleanly and completely removing it if you no longer find it useful; but, and this is a "Biggie", when you upgrade to the next version of Ubuntu it should, automatically upgrade all installed (through Synaptic) packages and programs. Not so for most of the ones that you manually installed.
Hope I didn't get too 'wordy', no pun intended.

:-)
Side

---

### Post by dragonwarriorfan on 2009-04-26
Sorry, I am using remix and there's a favorites tab. I can't get the new program in to the general area so that I might drop it to favs. Oh, thanks for the tip on searching for programs, Sidewinder, that really helps!

---

### Post by Sidewinder1 on 2009-04-27
Dmi

---

### Post by eilios on 2009-04-27
Dragon, to do that create a text file and type
"cd (destination)
./(file you opened with terminal)"
Then go into terminal and find that text file and type chmod a + x (text file)
and put it in your favourites.
 
For example
"cd /home/eilios/Documents
./game.sh"
Then go into terminal and type
"cd /home/eilios/Documents
chmod a + x gamerunner"
 
Then from there open it like a normal file.

---

