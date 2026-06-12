---
title: "How to manually install a program?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by phildred on 2009-06-07
Hello everyone, I'm brand new to linux and I have a question regarding the installation of downloaded programs. I tried to install flash player 10 by downloading it from adobe.com and installing it via the terminal with no luck. The same situation with vuze. I ended up installing them both with synaptic.

Long story short, I installed flash to home/phil/.mozilla and my main browser I use (opera) couldn't access flash sites but firefox could. And I couldn't even install vuze at all. Why did flash automatically install there and opera couldn't access flash sites? And how exactly should I have installed flash? Here are the two commands I used.

cd ~/Desktop/install_flash_player_10_linux
./flashplayer-installer

Thanks for your help.

---

### Post by aysiu on 2009-06-07
You should have installed Flash by using the package manager to install *adobe-flashplugin* or *flashplugin-nonfree*.

More details here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by mgt_90 on 2009-06-07
We might need a little more information than "with no luck." Did you get any error messages? What were they?  The commands for installing the proprietary flash plugin seem correct, so long as you unpacked the tarball.  But what you should really do is go back to Adobe's website and download the .deb file. It's packaged for Ubuntu, so you might as well use it.

---

### Post by pbpersson on 2009-06-07
I always use synaptic to install software because it "just knows" what needs to be done.

I am assuming you installed this while logged on as Phil.

Is that what the installation instructions told you to do, or were you supposed to install it using sudo so it would install on the system and make system-wide changes for you?

---

### Post by Fully216 on 2009-06-08
Keep in mind, since you are new linux user, installing packages may require other libraries/dependencies.  Synaptic or a packaged deb installation file takes care of this, which is why it is nice.

There are many places you can compile code from source.  I usually use ./usr/src but that is just my preference.  I install a link to the application (like OneSwarm for example) in the Applications menu because such things are not automatic if you are compiling code.

---

### Post by phildred on 2009-06-08
I don't know what happened with flash player, there was no error message it just told me that it was installed to home/phil/.mozilla and the vuze error gave me this:

Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest: No such file or directory
ls: cannot access /usr/java: No such file or directory
ls: cannot access /usr/lib/jvm/latest: No such file or directory
ls: cannot access /usr/lib/jvm: No such file or directory
Re-checking with GCJ (Sun Java recommended)..
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm: No such file or directory
OOPS, unable to locate java exec in  /usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)

which says to me that I don't have java installed. But I would have thought that if flash player didn't give any errors and said it was installed to the home/phil/.mozilla directory it would have worked. I ended up using synaptic to install them and I think I'll use that if I can but it's nice to know how to do it manually if I have to.

@ Fully216 I have no idea what you just said, I still have a lot to learn.

---

### Post by CJ Master on 2009-06-08
Did you try to use Add/Remove to install Vuze?

[Click here](apt:vuze) to install Vuze, then try accessing it by Going to Applications -> Internet -> Vuze

(I belive that Vuze is an internet program, torrenting right? And if the link I gave doesn't work then search for Vuze in Applications -> Add/Remove.)

---

### Post by roharme on 2009-06-08
.deb softwares are like .exe in Windows

You can install just by doing double click.

Try to get softwares in such formats for easy going.

Even if you get a rpm format its well and good, you can use Alien

---

### Post by CJ Master on 2009-06-08
> **roharme said:**
> 
Even if you get a rpm format its well and good, you can use Alien

I would highly recommend against this, alien causes nothing but trouble. Dig deeper for software, generally you can find some sort of DEB file. Or look in Synaptic for tons of different packages. (System -> Administration -> Synaptic Package Manger)

---

### Post by zvacet on 2009-06-08
@ **phildred**

You need Java for Vuze.If you don't have it itstalled then type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

That way you will install flash,Java...

You can find and download Vuze [here.]("http://www.getdeb.net/search.php?keywords=vuze") After download just double click on deb file.

---

### Post by pbpersson on 2009-06-11
> **phildred said:**
> 

which says to me that I don't have java installed. But I would have thought that if flash player didn't give any errors and said it was installed to the home/phil/.mozilla directory it would have worked.

No, if you install the software manually and the shell script is setup to only install the software, that is all that will happen.  It does not check to see if all the libraries, utilities, and other dependencies are in place.  However, the web site in the installation instructions should have listed all the dependencies for you.

On the other hand, a .DEB file (which is a Debian package file) or the Synaptic Package Manager (which is also dealing with .DEB files) will handle that all for you because when the .DEB file was created the creators specified all the dependencies for you.

---

