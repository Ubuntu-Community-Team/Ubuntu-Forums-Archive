---
title: "problem installing winexe client on ubuntu"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by arun chauhan on 2009-11-27
[B]Hello, I have successfully downloaded the source code for winexe client and have untared it but when i go for the command _./autogen.sh_ this is what i get


[/B]arun@ubuntu:~/winexe-source-081123$ sudo ./autogen.sh
./autogen.sh: running script/mkversion.sh
./script/mkversion.sh: 'version.h' created for Samba("4.0.0tp4-SVN-build-UNKNOWN")
./autogen.sh: running autoheader -I. -Ilib/replace
build/m4/check_cc.m4:8: error: AC_REQUIRE: circular dependency of AC_GNU_SOURCE
lib/replace/autoconf-2.60.m4:169: AC_USE_SYSTEM_EXTENSIONS is expanded from...
../../lib/autoconf/specific.m4:332: AC_GNU_SOURCE is expanded from...
lib/replace/autoconf-2.60.m4:169: AC_USE_SYSTEM_EXTENSIONS is expanded from...
build/m4/check_cc.m4:8: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
autoheader: '/usr/bin/autom4te' failed with exit status: 1
[B]
Can somebody help me installing this thing.
Thanx in advance...[/B]

---

### Post by Buuntu on 2009-11-27
The problem could be because your are using root privelages to run the autogen.sh, try running it without 'sudo'.  Also if that doesn't work, you could try the already compiled version available here: [http://eol.ovh.org/winexe/#how_to_get_it](http://eol.ovh.org/winexe/#how_to_get_it)

---

### Post by arun chauhan on 2009-11-28
> **Buuntu said:**
> The problem could be because your are using root privelages to run the autogen.sh, try running it without 'sudo'. Also if that doesn't work, you could try the already compiled version available here: [http://eol.ovh.org/winexe/#how_to_get_it](http://eol.ovh.org/winexe/#how_to_get_it)
 
 
before using sudo i tried it without root privileges but it was not working.... any ways can u guide me how to install this already compiled version.....
Thanks in advance...

---

### Post by Buuntu on 2009-11-28
Sure, try running this in the terminal:
```
wget http://eol.ovh.org/winexe/winexe-static-081123.bz2
bunzip2 winexe-static-081123.bz2
chmod a+x winexe
./winexe
```
Tell me if that works

---

### Post by arun chauhan on 2009-11-29
**Hey i tried running the above commands.... but this is wat i go**t


arun@ubuntu:~$ wget [http://eol.ovh.org/winexe/winexe-static-081123.bz2](http://eol.ovh.org/winexe/winexe-static-081123.bz2)
--2009-11-29 13:33:56--  [http://eol.ovh.org/winexe/winexe-static-081123.bz2](http://eol.ovh.org/winexe/winexe-static-081123.bz2)
Resolving eol.ovh.org... 213.251.131.44
Connecting to eol.ovh.org|213.251.131.44|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1254951 (1.2M) [application/x-bzip2]
Saving to: `winexe-static-081123.bz2'

100%[======================================>] 1,254,951   89.3K/s   in 14s     

2009-11-29 13:34:11 (90.2 KB/s) - `winexe-static-081123.bz2' saved [1254951/1254951]

arun@ubuntu:~$ bunzip2 winexe-static-081123.bz2
arun@ubuntu:~$ chmod a+x winexe
chmod: cannot access `winexe': No such file or directory

[B]it seems it's not recognizing this winexe directory...... and please can u give me a brief know how of what these commands will exactly do.........
Thanxs once again[/B]

---

### Post by bumanie on 2009-11-29
If the download is going to your desktop, you first need to change to there. In terminal > cd ~/Desktopthen do the commands. If it is downloaded elsewhere, you need to cd <to that direstory> eg > cd /home/<username>if downloaded to /home - I don't know the program, but a common mistake is not changing to the correct directory where the downloaded file is, before running install commands.

---

### Post by Buuntu on 2009-11-29
Yeah do what Bumanie said - change directory to wherever your downloads go with 'cd'.  
Brief summary of the commands I told you to run:
wget URL - downloads whatever is at the URL (in this case a program)
bunzip2 - unzips a program compressed with the program bunzip
chmod a+x file - grants executable permissions for all users to the file
./program - runs the program in the current directory called 'program'

---

### Post by arun chauhan on 2009-11-29
**hey thanks guys.... i got it but its not working as just ./winexe but when i typed the following it worked..... **

arun@ubuntu:~$ ./winexe-static-081123
winexe version 0.90
This program may be freely redistributed under the terms of the GNU GPL
Usage: winexe-static-081123 [-?|--help] [--usage] [-d|--debuglevel DEBUGLEVEL]
        [--debug-stderr] [-s|--configfile CONFIGFILE] [--option=name=value]
        [-l|--log-basename LOGFILEBASE] [--leak-report] [--leak-report-full]
        [-R|--name-resolve NAME-RESOLVE-ORDER]
        [-O|--socket-options SOCKETOPTIONS] [-n|--netbiosname NETBIOSNAME]
        [-W|--workgroup WORKGROUP] [--realm=REALM] [-i|--scope SCOPE]
        [-m|--maxprotocol MAXPROTOCOL] [-U|--user [DOMAIN\]USERNAME[%PASSWORD]]
        [-N|--no-pass] [--password=STRING] [-A|--authentication-file FILE]
        [-S|--signing on|off|required] [-P|--machine-pass]
        [--simple-bind-dn=STRING] [-k|--kerberos STRING]
        [--use-security-mechanisms=STRING] [-V|--version] [--uninstall]
        [--reinstall] [--system] [--runas=[DOMAIN\]USERNAME%PASSWORD]
        [--interactive=0|1] [--ostype=0|1|2] //host command

[B]THANKS A LOT.....
[/B]

---

