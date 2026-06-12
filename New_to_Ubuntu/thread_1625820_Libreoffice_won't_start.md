---
title: "Libreoffice won't start"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by beew on 2010-11-19
Hi,

I have installed libreoffice through a ppa (one and only) and it has been working great until the latest upgrade two days ago. Now it would not start. 

When I click a launcher (for writer,say, but same with others) I get
> Failed to execute child process "libreoffice" (No such file or directory)

Typing "libreoffice" in the terminal I get "command not found".

All the libreoffice files are in /opt/libreoffice, I tried to make a symbolic link with
```
sudo ln -s /opt/libreoffice /usr/local/bin/libreoffice

``` but that doesn't work. I click the launchers and it says permission denied.

I would appreciate any suggestion. Thanks.

---

### Post by beew on 2010-11-20
bump!

---

### Post by jtarin on 2010-11-20
You get permission denied because you don't own the file....it belongs to root. Make your link as root then authorize user to execute your link. You could probably add "sudo" to your launcher command.

---

### Post by yeats on 2010-11-20
> When I click a launcher (for writer,say, but same with others) I get

What command is the launcher trying to execute?  You can learn this by going to System -> Preferences -> Main Menu and select Edit for the menu item.

> You could probably add "sudo" to your launcher command.

You *could* do this, but it's not good practice to run your regular programs as root.  I think it's a better idea to get down to the bottom of what's going wrong before doing this or any other workarounds.

---

### Post by beew on 2010-11-20
Hi, chrissharp123

Sorry for not being clear, the commands in the launcher are something like > libreoffice -writer %UI don't want to run libreoffice as root, it should not be necessary. I think the upgrade just messed up something  minor and there should be a less drastic fix.

---

### Post by beew on 2010-11-20
> **jtarin said:**
> You get permission denied because you don't own the file....it belongs to root. Make your link as root then authorize user to execute your link.


How do I authorize users to execute my link? Thanks.

---

### Post by beew on 2010-11-21
Bump!

---

### Post by beew on 2010-11-22
Bump! Hello, anyone?

---

### Post by beew on 2010-11-23
Bump!!! I wish there is an autobump setting.

---

### Post by wanchai on 2010-11-23
Have you tried to launch it from the command line?

I installed LibreOffice from the deb files that I downloaded from their website. The install did not create any launchers or menu entries. However, I can go to [FONT="Courier New"]/opt/libreoffice/program[/FONT] and then run, for example [FONT="Courier New"]soffice[/FONT] or [FONT="Courier New"]swriter[/FONT]. Apparently, the version I have is still using the same file names as OpenOffice (and StarOffice?). All the files and directories belong to root. However, everybody has read and execute rights. Please check this on your installation. Once you figured out how to start LibreOffice from the command line, the launchers or menus shouldn't be that difficult.

---

### Post by beew on 2010-11-24
> **wanchai said:**
> Have you tried to launch it from the command line?



Yes, I have. As I said in my first post I got "command not found". I installed with a PPA and it created the launchers and everything. In has always worked flawlessly until the recent update.

Here is info for the PPA install.[ http://www.omgubuntu.co.uk/2010/10/install-libreoffice-ppa-ubuntu/]("http://www.omgubuntu.co.uk/2010/10/install-libreoffice-ppa-ubuntu/")

---

### Post by wanchai on 2010-11-24
Can you please post the output of [FONT="Courier New"]ls -l /opt/libreoffice/program[/FONT] ?

---

### Post by beew on 2010-11-25
Hi,

Thanks for the reply. Here they are
> -r--r--r-- 1 root root  9246 2010-11-14 20:04 about.png
-r--r--r-- 1 root root  8427 2010-11-14 20:04 about-pt_BR.png
-r--r--r-- 1 root root   197 2010-11-14 20:04 bootstraprc
-r--r--r-- 1 root root  1332 2010-11-14 20:04 fundamentalrc
-r--r--r-- 1 root root 24676 2010-11-14 20:04 intro.png
-r--r--r-- 1 root root 22650 2010-11-14 20:04 intro-pt_BR.png
-r-xr-xr-x 1 root root 78448 2010-11-14 20:05 kdefilepicker
-r-xr-xr-x 1 root root 22604 2010-11-14 20:04 libnpsoplugin.so
-r-xr-xr-x 1 root root  2491 2010-11-14 20:04 python
-r--r--r-- 1 root root    50 2010-11-14 20:04 redirectrc
-r-xr-xr-x 1 root root    61 2010-11-14 20:05 sbase
-r-xr-xr-x 1 root root    61 2010-11-14 20:08 scalc
-r-xr-xr-x 1 root root    61 2010-11-14 20:04 sdraw
-r--r--r-- 1 root root    53 2010-11-14 20:04 setuprc
drwxr-xr-x 2 root root  4096 2010-11-18 04:36 shell
-r-xr-xr-x 1 root root    64 2010-11-14 20:05 simpress
-r-xr-xr-x 1 root root    61 2010-11-14 20:04 smath
-r-xr-xr-x 1 root root  4674 2010-11-14 20:04 soffice
-r-xr-xr-x 1 root root  6620 2010-11-14 20:04 soffice.bin
-r--r--r-- 1 root root   191 2010-11-14 20:04 sofficerc
-r-xr-xr-x 1 root root  2722 2010-11-14 20:04 spadmin
-r-xr-xr-x 1 root root    63 2010-11-14 20:08 swriter
-r-xr-xr-x 1 root root  1803 2010-11-14 20:04 unoinfo
-r-xr-xr-x 1 root root  2754 2010-11-14 20:04 unopkg
-r-xr-xr-x 1 root root  6448 2010-11-14 20:04 unopkg.bin
-r--r--r-- 1 root root   363 2010-11-14 20:04 versionrc



---

### Post by wanchai on 2010-11-25
Ok, then try to run [FONT="Courier New"]/opt/libreoffice/program/soffice[/FONT] or [FONT="Courier New"]/opt/libreoffice/program/scalc[/FONT] or [FONT="Courier New"]/opt/libreoffice/program/soffice -writer[/FONT] .

If that works, then change your launchers and/or menu entries to point to these binaries. Apparently you were trying to run a binary (libreoffice) that simply doesn't exist (anymore?).

You don't really need the link to /usr/local that you created earlier. If you do have OpenOffice.org on your machine, I suggest that you launch LibreOffice using the full path names as shown above because the names of the binaries are the same in both versions. If you do not have OpenOffice.org installed, then make sure that [FONT="Courier New"]/opt/libreoffice/program[/FONT] is in your [FONT="Courier New"]$PATH[/FONT] variable. The command [FONT="Courier New"]which soffice[/FONT] will tell you which soffice the system finds when you're trying to run [FONT="Courier New"]soffice[/FONT] without the complete path. There are several ways to set the search path, the system wide setting is in [FONT="Courier New"]/etc/environment[/FONT].

---

### Post by beew on 2010-11-26
Yes, entering the full path opens the program,  but how to I open a document by right clicking? I enter /opt/libreoffice/program/swriter as the command in the "open with" tab and when I click the document I get an error message > The application cannot be started. 
[context="user"] caught unexpected exception!

Thanks again!

---

### Post by beew on 2010-11-27
bump!

---

### Post by beew on 2010-11-28
Bump!

---

### Post by beew on 2010-11-29
Ok, if I set the command of the launcher (for writer) as ```
/opt/libreoffice/program/swriter %U
``` then it works, right click on a document and it opens.

But now I have a different problem concerning making aliases (so hopefully there are more responses, I hate having to bump the thread continuously!)

I tried to make an alias by typing

```
alias 'Libreoffice -writer'='/opt/libreoffice/program/swriter'
```
It said the name is not valid.

Removing the space, ```
alias 'Libreoffice-writer'='/opt/libreoffice/program/swriter'
``` works. I put ```
Libreoffice-writer %U
``` in the launcher's command box, but then right clicking a document no longer opens it.

Also, in my experimenting I somehow created an alias ```
-writer='/opt/libreoffice/program/swriter'
``` I tried to remove it with the unalias command but keep getting -w is not a valid option.

Any help please?

---

