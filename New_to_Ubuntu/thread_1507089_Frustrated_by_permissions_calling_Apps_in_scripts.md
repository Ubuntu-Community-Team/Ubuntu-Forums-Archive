---
title: "Frustrated by permissions calling Apps in scripts"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by voxmagna on 2010-06-11
Hi, I'm struggling with writing basic scripts or running scripts written by others which appears to be connected with 'permissions'. The scripts written by others for other distros work.

Here's my simple example:

Network manager processes are stopped to allow iwconfig changes.

I can type *sudo iwconfig wlan2 channel 5* at the command prompt and after a password request the command is executed and I can confirm my wireless adaptor is on channel 5 with iwconfig.

But if I call iwconfig from within a (tcl) script:

[I]1 #!/usr/bin/tclsh
2 exec iwconfig wlan2 channel 5
3 exit[/I]

There is no execution.

It's the same if I try calling other apps within a script that would normally need sudo at the command prompt.

Can a global permission be assigned to a script so that all Apps called will run?

Can I disable sudo or rather enable it for all instances?

I'm not even off the starting grid yet!

Thanks

---

### Post by Drenriza on 2010-06-11
cant you make a bash script and add

```
sudo -u root /path/to/the/command
```

or change your sudoers file to allow the command without password
```
username ALL=NOPASSWD: /path/to/command
```

then you type ```
sudo iwconfig wlan2 channel 5
``` but you wont be asked to enter your password

---

### Post by squaregoldfish on 2010-06-11
If the command you want to run requires sudo, then any script you write that contains that command will also require sudo.

So, for your tcl script you can either call

```
sudo <script>
```or change the exec command to include the sudo qualifier

```
exec sudo iwconfig wlan2 channel 5
```In either case, you'll be asked for the password as normal.

Steve.

---

### Post by Drenriza on 2010-06-11
i just tested ```
sudo -u root /path/to/the/command
```

in a small script to open visudo or apt-get update
and i dont get prompted for a password. It just do it! ,)
```
sudo -u root /usr/sbin/visudo
```

---

### Post by voxmagna on 2010-06-11
Thanks, I'm going to try the suggestions. But please tell me, is Ubuntu different to other distros, because if I look at scripts written by others I don't see a sudo anywhere?

---

### Post by Jakiejake on 2010-06-11
> **voxmagna said:**
> Thanks, I'm going to try the suggestions. But please tell me, is Ubuntu different to other distros, because if I look at scripts written by others I don't see a sudo anywhere?

What other distros are you talking about?

---

### Post by voxmagna on 2010-06-11
Hi, Fedora.

The suggestions have worked - Thanks!

One thing I'm puzzled over is paths in scripts written by others are often not where Ubuntu seems to hold the apps that get called in the script. I've had to use the (slow) Nautilus file search to discover they aren't where the script points to.

Being a total newbie - is this normal, does Ubuntu depart from any 'conventions' during its install, or is there no convention and you have to edit scripts changing path statements for Ubuntu?

Or do I need to write a script which parses scripts to make the paths Ubuntu compatible?

Thanks

---

### Post by tarps87 on 2010-06-11
If you want to find the path to an app usally it is in a bin folder so just type
```

which *appName*

```
A lot of ditros differ as to how files are managed and where they are stored.
Where are you getting these scripts from?

---

