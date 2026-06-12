---
title: "How To Install tar.gz files In/On Xubuntu"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by faron45 on 2010-03-15
Okay,everybody. I just don't know what to do anymore.I'm just so confused by this whole issue.I have a file on my desktop called flashplayer10_1_p3_linux_022310.tar.gz that I would like to install & try.But,I just can't for the life of me figure out how to install this thing.And,I've basically been  searching out how to do this for the last couple of days now.Any help out there with this ? I am soooooooo completely frustrated by this.

And,if anybody knows of a GOOD place I can go to to learn how to download & install packages on my Xubuntu system I would GREATLY appreciate it {think to yourself...this guy's a beginner with computers}And,remember,please,I asked for a GOOD place {Ha,ha}.Again,I'm sorry.I'm just so frustrated.

Thanks much all

Extra info...I have installed the latest {3.6} Firefox on my system & there are some things on my system that now need to be fixed.And,my flashplayer is one of those things.After install of 3.6 I have noticed under add-ons -extensions that noscript & Ubuntu Firefox Modifications are incompatible & disabled.I have also noticed under add-ons-plugins that in addition to the lates version of shockwave flash that I had installed {vers 10.0 r45},FF vers 3.6 comes with version 0.4.12 of shockwave flash.And,apparently,it also comes with vers 0.96.1 of gcj web browser plugin & xine plugin vers 1.0.1.

---

### Post by mikewhatever on 2010-03-15
You don't install that file, just unpack the content to .mozilla/plugins. Before you do that, can you explain what's the problem with Firefox3.6 and flash player 10.0r45.

---

### Post by faron45 on 2010-03-15
I'm not really sure what the problem is.All I know is that after install I had all that extra stuff in the add-ons-plugins & flashplayer just wouold not work.I even disabled everything to try & troubleshoot it allEven that didn't work.So,I've uninstalled all plugins to reinstall them.And,thanks for your help by the way.

Also,if I may ask...Noscript & Ubuntu Firefox Modifications being incompatible with vers 3.6,would you suggest I just go ahead & uninstall those ?

---

### Post by VoodooLoveDog on 2010-03-15
If you are coming from a Windows world, Linux can be confusing when it comes to "installer" files. 

A tar.gz is a tarball file or a file that collection of compressed files. Not unlike a zip file. Run the following code to uncompress the tarball:

```
tar xvzf /path_to_file/name_of_file
```

That will expand the contents of the file into a folder that has the same name as the tarball. You'll end up with one of two things. Either you will have a binary or a collection of files to install. I believe the flash software is a binary.

Run this code on the binary:

```
sudo ./name_of_binary
```

Depending on where you are running it from, you may need to allow it to execute:

```
chmod a+x name_of_file
```

That will invoke the installer process and install the software on the computer. I suggest taking a look at the install instructions on Adobe's web site to complete any additional tasks (e.g. setting up symbolic links for browser plugins). 

In the case of this software, it's way easier to install one of my favorite pieces of software (Ubuntu Tweak: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)) and then install flash and lots of other goodies from there.

If you end up trying to install a tarball that is a collection of files you need to compile, take a look at this site to understand the process:

[http://www.codecoffee.com/tipsforlinux/articles/27.html](http://www.codecoffee.com/tipsforlinux/articles/27.html)


Hope this helps.

---

### Post by mikewhatever on 2010-03-15
> **faron45 said:**
> ...

Also,if I may ask...Noscript & Ubuntu Firefox Modifications being incompatible with vers 3.6,would you suggest I just go ahead & uninstall those ?

Try uninstalling the addons and then reinstalling. Not quite sure what's up there. Another thing to do is completely remove the existing version of flash player.

sudo apt-get purge flashplugin-installer

---

### Post by faron45 on 2010-03-16
voodoolovedog...what do you think of this ?
tar xvzf /desktop/flashplayer10_1_p3_linux_022310.tar.gz
tar: /desktop/flashplayer10_1_p3_linux_022310.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I don't think I got that "path" thing right.

---

### Post by VoodooLoveDog on 2010-03-16
> **faron45 said:**
> voodoolovedog...what do you think of this ?
tar xvzf /desktop/flashplayer10_1_p3_linux_022310.tar.gz
tar: /desktop/flashplayer10_1_p3_linux_022310.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I don't think I got that "path" thing right.

Yes. Your path is incorrect. Another gotcha from windows. Windows could care less about upper or lower case characters in folder or file names. 

so: c:\windows\system32 is no different to windows as C:\WinDows\SyStem32

Linux is different. /home/Desktop/ is different than /home/desktop/

Remember you are operating from the home directory on the pc. Rather than using a relative path, use the full path to file:

```
/home/YOUR_USER_NAME/Desktop/flashplayer10_1_p3_linux_022310.tar.gz
```

You can also abbreviate /home/YOUR_USER_NAME with ~

So your command would be:

```
tar xvzf /home/YOUR_USER_NAME/Desktop/flashplayer10_1_p3_linux_022310.tar.gz
```

or 

```
tar xvzf ~/Desktop/flashplayer10_1_p3_linux_022310.tar.gz
```

or....

you could change directory (cd) to your desktop and then run the command from with in the folder.

```
cd /home/YOUR_USER_NAME/Desktop/
tar xvzf flashplayer10_1_p3_linux_022310.tar.gz
```

Take a look at some links that have basic linux command tutorials to have a better understanding of the terminal.

---

### Post by faron45 on 2010-03-16
thanks again very much everybody

---

### Post by mikewhatever on 2010-03-16
> **bacchusmarsh said:**
> i don't know which name-of-file unfortunately as it is now unpacked as the 3 files above.

I can't figure out how to use aircrack-ng, and can't get the GUI of that going either:???:

You probably shouldn't be installing wepcrack in the first place, let alone asking for help here. Do you have any legitimate, Ubuntu related questions?

---

### Post by bacchusmarsh on 2010-03-16
fair enough, i probably shouldn't be trying to wepcrack, i was simply wondering if you could patch into wireless internets while mobile, as a way of quickly checking mail etc. I guess people consider that 'steeling' but i am all for common resources.

My ubuntu related issue is trying to install programs that are downloaded as tar.gz. every guide i have followed i seem to get lost pretty quickly.

never mind, i have wasted enough time on it already. Sorry for the misunderstanding.

---

