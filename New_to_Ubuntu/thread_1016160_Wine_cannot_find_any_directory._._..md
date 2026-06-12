---
title: "Wine cannot find any directory. . . ?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-12-19
I just installed Wine and attempted to use it to run the Google Chrome installer, but I get the following output:

```
travis@travis-laptop:~$ wine /home/travis/Desktop/ChromeSetup.exe
Warning: could not find DOS drive for current working directory '/home/travis', starting in the Windows directory.
wine: cannot find '/home/travis/Desktop/ChromeSetup.exe'
travis@travis-laptop:~$ 

```

I tried just double clicking on the .exe with no response whatsoever. (proving the terminal's superiority to the GUI)  I also tried some different .exe files in different directories but with no avail.


What can I do to fix this?

Thanks in advance!

---

### Post by taurus on 2008-12-19
After you installed wine from the repos, did you configure it first before you use/run it?

```
winecfg
```
Also, make sure ChromeSetup.exe is in ~/Desktop.

```
ls -la ~/Desktop
```

---

### Post by pi.boy.travis on 2008-12-19
Yes.  Everything looks normal, here are some screenshots:

[ATTACH]96935[/ATTACH]

[ATTACH]96936[/ATTACH]

[ATTACH]96937[/ATTACH]

[ATTACH]96938[/ATTACH]

Thanks

---

### Post by mc4man on 2008-12-19
Go back into winecfg -> drives and click 'autodetect'

---

### Post by pi.boy.travis on 2008-12-19
OK, got past the last error, but now I have this:


```
travis@travis-laptop:~$ wine /home/travis/Desktop/ChromeSetup.exe
fixme:advapi:CheckTokenMembership ((nil) 0x12da30 0x33fb50) stub!
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:winhttp:WinHttpOpen ((null), 1, (null), (null), 0x0): stub
travis@travis-laptop:~$ 

```

I'm haven't used wine before, so I'm not quite sure what to make of this. . .   What can I do?

Thanks!

---

### Post by pi.boy.travis on 2008-12-19
OK, the Opera installer worked. . . but why won't Google Chrome?  Do I need to add libraries?

Thanks!

---

### Post by Daveth on 2008-12-19
um, it is not looking good.....

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8177](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8177)

---

### Post by mc4man on 2008-12-19
> but why won't Google Chrome?

I don't believe it's that simple, try googling Google Chrome in ubuntu.

Ex.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13635)

[http://www.fixya.com/support/r1238728-install_google_chrome_ubuntu](http://www.fixya.com/support/r1238728-install_google_chrome_ubuntu)

I wouldn't bother, good luck though.

---

