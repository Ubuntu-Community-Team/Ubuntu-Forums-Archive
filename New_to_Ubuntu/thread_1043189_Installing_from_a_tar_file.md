---
title: "Installing from a tar file"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by aarmbruster on 2009-01-18
Hello,

I am attempting to install a program called serproxy that allows ports to be access through socket connections. The install direction that comes with serproxy state that, in terminal, you type ```
make
``` while in the serproxy folder to compile. That seems to go ok. Next you are suppose to type ```
make install
```, and this is where the issue arises. Terminal gives me the error
```
cp -f serproxy /usr/local/bin
cp: cannot create regular file `/usr/local/bin/serproxy': Permission denied
make: *** [install] Error 1
``` You can find the serproxy download [[COLOR="Blue"]here[/COLOR]]("http://www.lspace.nildram.co.uk/files/serproxy-0.1.2.tar.gz"). Thank you in advance for any help. 

Andrew

---

### Post by Nepherte on 2009-01-18
You don't have sufficient permissions to install it. Use the sudo prefix to acquire temporary root priviliges:
```
sudo make install
```

---

### Post by aarmbruster on 2009-01-18
Thank you for the reply Nepherte. That command worked great and moved the serproxy executable to the usr/local/bin location. I now have the issue where the executable doesn't do anything when i try to run it. I tried dragging the executable into terminal and it gave me the error "Couldn't find 'comm_ports' entry in config file '/etc/serproxy.cfg'". I assumed that serproxy is attempting to access the .cfg file in a sub folder called etc(?), but I created an etc folder and placed a cfg file in it with the same result (on a side note, the cfg file does have the 'comm_ports' entry Terminal was looking for ). Do you have any suggestions as to what I should try next? Thanks.

Andrew

---

### Post by Nepherte on 2009-01-18
How about launching serproxy from the terminal supplying the full path?
```
/usr/local/bin/serproxyexecutablename
```

Unfortunately I'm not aware of its configuration.

---

### Post by baruch60610 on 2009-01-18
Aarmbruster, you didn't need to create an 'etc' folder.  There is already one at /etc/  That preceding slash is very important.  It tells the system to look for the directory right under the root directory (the root directory is '/').  The /etc/ directory is a very imporant, system-wide directory where many vital configuration files live.

What you need to do is to go to /etc and check whether there exists any such file as setproxy.cfg.  Chances are, it doesn't exist.  So try this:

```
ls -l /etc/setproxy*
```That should show any files related to setproxy, if any exist.  If none exist, then you'll need to use a text editor as root, to create one and add the desired information.  So you could do:

```
 sudo nano /etc/setproxy.cfg
```for example, if you're familiar with nano.  Use whatever text editor you're comfortable with, but NOT a word processor.  If it allows you to format your text, it's going to make a mess of the config file, so use kate, nano, vim, emacs, gedit, or a similar plain text editor.  But you'll need to do this as root, not as a regular user, because users can't write to the /etc/ directory.

Also, you should be able to run your installed program simply by going to a terminal and typing its name.  It should be in your path - your PATH variable should include /usr/local/bin/.  To make sure, go to a terminal and type:

```
echo $PATH
```That should give you something that looks like this:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```As you can see, /usr/local/bin is among the paths included in the PATH variable.

HTH.

---

### Post by aarmbruster on 2009-01-18
Thanks for the help guys. I followed your suggestions and am having the same issue as before. When I attempt to run serproxy, terminal gives me the response```
Couldn't find 'comm_ports' entry in config file '/etc/serproxy.cfg'
``` I dont' fully understand the /etc/ folder and why the serproxy config file would be placed there. It is my understanding that the config file needs to reside in the same folder as the serproxy executable. Just a couple of questions to help understand this a little better:

Is the /etc/ folder at usr/local/etc the same as the one serproxy is looking for?

Why would other executables that I have downloaded run on a double click (or give me the option to "Run in Terminal" on RMB), but the serproxy executable does not? Is it possible that I have improperly compiled the executable?

Thanks again guys (and gals:)).

Andrew

---

### Post by redseventyseven on 2009-01-18
> It is my understanding that the config file needs to reside in the same folder as the serproxy executable. Just a couple of questions to help understand this a little better:

Um... no. That's not how the Linux filesystem works - it's rather different from Windows I'm afraid. Have a little read of this article - it's quite old but it explains how the folders are arranged and what each folder's purpose is. [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

Instead of dumping everything in the "System" folder (like with Windows), there are different folders assigned to essential binary files (/sbin and /bin), programs (/usr), libraries - similar to Windows .dll files (/lib) and config files (/etc). Your program is expecting to find its configuration file in the usual (for Linux that is) place.

Just to make it even more complicated, configuration files come in two types - system-wide (every user of the computer can access them) and user-specific (self-explanatory). For a program like your serproxy, it's likely that the network settings would need to be reproduced for all users of the computer, hence they need to store configuration settings in /etc. Other things require different configs for different users, for example, your Appearance settings - these are stored in their own sub-folders of your home folder. The other executables that you were able to run simply by double clicking because they don't rely on system-wide libraries or configuration files will fall into this category. If you navigate to your home folder and reveal the hidden files you will notice lots of files and folders (beginning with a ".") that contain your personal settings for programs that you run.

Hope that helps explain things!

---

### Post by aarmbruster on 2009-01-19
Ok, so serproxy is working like a dream now. I wasn't properly writing out the config file using nano. To those new users out there, like myself, if you need to write a cfg file to /etc/ follow the directions provided earlier in this post using nano, type or paste in the appropriate content and use ctrl-o to write the file.

Andrew

---

