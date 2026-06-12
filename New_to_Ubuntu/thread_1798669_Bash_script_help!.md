---
title: "Bash script help!"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by junkyhlm on 2011-07-06
Hi im trying to make a simple script to launch my wine instance of WormsReloaded trough XMBC. I've gotten my script to 

1. Kill XBMC and wait for it to be properly finished
2. Start WormsReloaded.exe

But then i get stuck. I want the script to start XBMC again when Worms is shut down. But i Cant get the bloody script to wait. It just starts XBMC right away.

Here's my script:
```
#!/bin/bash

sh /home/holmen/script/kill_xbmc
wait

env WINEPREFIX="/home/holmen/.wine" wine C:\\windows\\command\\start.exe /Unix /home/holmen/.wine/dosdevices/c:/$
wait

xbmc -fs

exit
```

Anyone that can help me?

---

### Post by wolfgangmcq on 2011-07-06
Wait requires a job ID.  Use ```
wait $?
``` instead. ($? is a bashism for the pid of the last process run.)

---

### Post by junkyhlm on 2011-07-06
Sweet, will try that. Thank you

---

### Post by junkyhlm on 2011-07-06
Did'nt help :/ it started xbmc right away.

when i run the script outside xbmc i get som errors when starting worms:

```

holmen@htpc:~$ sh script/start_worms 
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
holmen@htpc:~$ fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
Crc::sCrc ==fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xded5b8,0xded9d8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xdeda68,0xded9d8): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:system:SystemParametersInfoW Unimplemented action: 79 (SPI_GETLOWPOWERTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 81 (SPI_SETLOWPOWERTIMEOUT)
err:mmtime:TIME_MMTimeStop Timer still active?!



```

And the promt does not return until i press a key.

---

### Post by Perkins on 2011-07-06
The worms command is launching worms and then exiting, which means that your wait command is detecting the launcher exit and moving on immediately.  You need to figure out what the name of the worms process is while it's running.  Then you can use pidof to get the number and wait to wait for it to end.

---

### Post by junkyhlm on 2011-07-07
> **Perkins said:**
> The worms command is launching worms and then exiting, which means that your wait command is detecting the launcher exit and moving on immediately. You need to figure out what the name of the worms process is while it's running. Then you can use pidof to get the number and wait to wait for it to end.
 
Thanks for the answer! I've changed the script into this but i can't try it until tonight. Does i look ok to you?
 
```
#!/bin/bash
sh /home/holmen/script/kill_xbmc
wait
env WINEPREFIX="/home/holmen/.wine" wine C:\\windows\\command\\start.exe /Unix /home/holmen/.wine/dosdevices/c:/users/Public/Skrivbord/Worms\ Reloaded.lnk
worms=`pidof WormsReloaded.exe`
waitpid $worms
xbmc -fs
exit

```

---

### Post by Perkins on 2011-07-07
That should work as long as the name of the Worms process is correct.

---

### Post by wafflesausage on 2011-07-07
> **wolfgangmcq said:**
> Wait requires a job ID.  Use ```
wait $?
``` instead. ($? is a bashism for the pid of the last process run.)

I thought that $? holds the value of the exit status of the last program executed from the shell.

---

### Post by josephmills on 2011-07-07
> **wafflesausage said:**
> I thought that $? holds the value of the exit status of the last program executed from the shell.

yes it does you are right

---

### Post by wolfgangmcq on 2011-07-08
Sorry, my fault. I meant $! instead. (See if that works any better.)

---

### Post by junkyhlm on 2011-07-11
> **junkyhlm said:**
> Thanks for the answer! I've changed the script into this but i can't try it until tonight. Does i look ok to you?
 
```
#!/bin/bash
sh /home/holmen/script/kill_xbmc
wait
env WINEPREFIX="/home/holmen/.wine" wine C:\\windows\\command\\start.exe /Unix /home/holmen/.wine/dosdevices/c:/users/Public/Skrivbord/Worms\ Reloaded.lnk
worms=`pidof WormsReloaded.exe`
waitpid $worms
xbmc -fs
exit

```
 
This generates error: "waitpid: command unknown". Does not quite understand how to use waitpid, have tried the man but it does not make me any smarter .
 
> **wolfgangmcq said:**
> Sorry, my fault. I meant $! instead. (See if that works any better.) 
 
This dont work, just starts XBMC right away. :/

---

### Post by Perkins on 2011-07-11
Most likely it's not finding the pid of WormsReloaded.exe.  That's what the "command not found" message usually means.  Start worms and then play with pidof and make sure it's returning a number for you.

---

### Post by junkyhlm on 2011-07-11
> **Perkins said:**
> Most likely it's not finding the pid of WormsReloaded.exe. That's what the "command not found" message usually means. Start worms and then play with pidof and make sure it's returning a number for you.
 
I've got a PID for WormsReloaded.e from pidof but it seems that waitpid is not a correct way to use it. When I type wait and then press tab is seems that wait is the only command named like this.
 
I've been experimenting with waitpid() commands from the manual but i cant get the damn thing to work :(

---

### Post by Perkins on 2011-07-11
Here's a perl script that will wait until WormsReloaded.exe disappears.


```

#! /usr/bin/perl

$worms=1;
while($worms==1)
{
  $worms=`ps -A |grep WormsReloaded.exe`;
  if($worms ne "")
  {
    $worms=1;
  }
}

```

Chain this in in place of your pidof and waitpid and it should work for you.

---

### Post by junkyhlm on 2011-07-11
> **Perkins said:**
> Here's a perl script that will wait until WormsReloaded.exe disappears.
 
 
```

#! /usr/bin/perl
 
$worms=1;
while($worms==1)
{
  $worms=`ps -A |grep WormsReloaded.exe`;
  if($worms ne "")
  {
    $worms=1;
  }
}

```
 
Chain this in in place of your pidof and waitpid and it should work for you.
 
OK, thank you. I'll try this when i get home. Sorry for beeing so noobish but how do i "chain" it properly to the rest of the code?
 
```

#!/bin/bash
sh /home/holmen/script/kill_xbmc
wait
env WINEPREFIX="/home/holmen/.wine" wine C:\\windows\\command\\start.exe /Unix /home/holmen/.wine/dosdevices/c:/users/Public/Skrivbord/Worms\ Reloaded.lnk

[B]perl wait_worms
worms=`pidof perl`[/B]
**waitpid $worms**

xbmc -fs
exit 

```
 
This does not feel right. Gaah, its confusing. I need to google some more. I just can't get how to use the waitpid command. I've tried every possible way soon :/
 
all I get is "waitpid: command not found" even with "waitpid --help" and just "waitpid"

---

### Post by Perkins on 2011-07-11
Throw away the two lines after perl wait_worms.  The script does the waiting for you.

---

### Post by Perkins on 2011-07-11
Oh, and idiot me forgot a line.  Make it:

```

#! /usr/bin/perl
 
$worms=1;
while($worms==1)
{
  sleep(10);
  $worms=`ps -A |grep WormsReloaded.exe`;
  if($worms ne "")
  {
    $worms=1;
  }
}
```And it won't eat all your cpu.

---

### Post by junkyhlm on 2011-07-11
> **Perkins said:**
> Oh, and idiot me forgot a line. Make it:
 
```

#! /usr/bin/perl
 
$worms=1;
while($worms==1)
{
  sleep(10);
  $worms=`ps -A |grep WormsReloaded.exe`;
  if($worms ne "")
  {
    $worms=1;
  }
}
```And it won't eat all your cpu.
 
Ok Thank you, but this means it'll wait for up to ten seconds before it starts XBMC again? I can live with that if it is the best way. :)

---

### Post by Perkins on 2011-07-11
Adjust the timing however you like.  You're probably ok to knock it down to one second.  Make it too short though and it will have a negative impact on your machine's performance since it'll be checking repeatedly as fast as it can.

---

### Post by dethorpe on 2011-07-11
> **junkyhlm said:**
> This generates error: "waitpid: command unknown". Does not quite understand how to use waitpid, have tried the man but it does not make me any smarter . :/
 
Don't think there is a waitpid bash command, just a system call (which is what the man page is refering to), just use wait with the pid as a prameter:
 
```
 
 wait $worms

```

---

### Post by Perkins on 2011-07-11
I think the problem he's running into with his attempted wait commands is that they only work on processes that are children of the invoking shell.  Since worms gets launched and then goes off on its own, it may or may not actually work right.

---

