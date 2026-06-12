---
title: "How do I create this script?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by xg7 on 2009-03-21
I need to create a script.  I have the script already, but I do not know how to create it at all.  Please help.

See here for description of issue...

[http://ubuntuforums.org/showthread.php?t=960898&highlight=flashing+wifi&page=3](http://ubuntuforums.org/showthread.php?t=960898&highlight=flashing+wifi&page=3)

Thanks a bunch! :)

---

### Post by logos34 on 2009-03-21
try this howto:
[http://ubuntuforums.org/showpost.php?p=1265101&postcount=2](http://ubuntuforums.org/showpost.php?p=1265101&postcount=2)

---

### Post by xg7 on 2009-03-21
Great, thanks.

The script tutorial says to start the script with "#! /bin/bash", but the scripts in the link I am following start with "#!/bin/sh".  Which one should I use?

---

### Post by logos34 on 2009-03-21
either one should work fine

---

### Post by xg7 on 2009-03-21
OK, so I opened a terminal and typed:

gedit /etc/network/if-up.d/noblink

...which (I guess) created a new file in if-up.d

Then, when that file appeared, I cut and pasted the recommended script into that file (not into the terminal).

Recommended script:

#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger

When I tried to save the file I get the message "Could not save the file /etc/network/if-up.d/noblink.  You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again. 

What should I do now? 
Thanks

---

### Post by amadeus266 on 2009-03-21
> **xg7 said:**
> OK, so I opened a terminal and typed:

gedit /etc/network/if-up.d/noblink

...which (I guess) created a new file in if-up.d



Try putting sudo in front of that command. You can't save files in /etc as a normal user.

---

### Post by irv on 2009-03-21
> **xg7 said:**
> OK, so I opened a terminal and typed:

gedit /etc/network/if-up.d/noblink

...which (I guess) created a new file in if-up.d

Then, when that file appeared, I cut and pasted the recommended script into that file (not into the terminal).

Recommended script:

#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger

When I tried to save the file I get the message "Could not save the file /etc/network/if-up.d/noblink.  You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again. 

What should I do now? 
Thanks

before gedit type sudo and enter your root password. You should be able to save the file

---

### Post by xg7 on 2009-03-21
I was able to save the file.  However, when I went to run it, I typed (in the terminal):

/etc/network/if-up.d/noblink

I received the message "bash: /etc/network/if-up.d/noblink: Permission denied

Thanks all.

---

### Post by amadeus266 on 2009-03-21
> **xg7 said:**
> I was able to save the file.  However, when I went to run it, I typed (in the terminal):

/etc/network/if-up.d/noblink

I received the message "bash: /etc/network/if-up.d/noblink: Permission denied

Thanks all.

Again you may have to use sudo.

---

### Post by xg7 on 2009-03-21
Alright, I place "sudo" in front of the command to look like this:

sudo /etc/network/if-up.d/noblink

I now get the message sudo: /etc/network/if-up.d/noblink: command not found

?

---

### Post by xg7 on 2009-03-21
Also curious if I have to enter the sudo command due to specific settings I have set up.  Do not all people have to enter the sudo/password?  When Ubuntu starts I have to enter a username and password.  Is there a way around this?

---

### Post by irv on 2009-03-22
> **xg7 said:**
> Also curious if I have to enter the sudo command due to specific settings I have set up.  Do not all people have to enter the sudo/password?  When Ubuntu starts I have to enter a username and password.  Is there a way around this?

Go to the menu: System> Administration> Login> Security tab. Put a check in the auto login. You may have to put your script in a public place for all to run it. and make sure you make it Excusable.

---

### Post by mlentink on 2009-03-22
> **irv said:**
> You may have to put your script in a public place for all to run it. and make sure you make it Excusable.


I guess you mean the OP needs to make it executable, like this
```
sudo chmod +x /path/to/file.sh
```

---

### Post by mlentink on 2009-03-22
> **xg7 said:**
> Also curious if I have to enter the sudo command due to specific settings I have set up.  Do not all people have to enter the sudo/password?  When Ubuntu starts I have to enter a username and password.  Is there a way around this?

The sudo system is based on the idea that for security purposes the 'root'-user is locked, cannot be used. To give certain users the privileges to perform 'root'-like actions as a Super User, they need to precede commands with the sudo command, which means something like 'as _***s***_uper _***u***_ser _***do***_:'. 

Hope this explains a bit, but you can find more info [here]("https://help.ubuntu.com/community/RootSudo")

---

### Post by xg7 on 2009-03-22
Thanks all - very helpful.

Back to the original problem, I created a script file successfully but cannot get it to run.

I placed "sudo" in front of the command to look like this:

sudo /etc/network/if-up.d/noblink

I now get the message sudo: /etc/network/if-up.d/noblink: command not found

Please help - thank you!

---

### Post by irv on 2009-03-22
> **xg7 said:**
> Thanks all - very helpful.

Back to the original problem, I created a script file successfully but cannot get it to run.

I placed "sudo" in front of the command to look like this:

sudo /etc/network/if-up.d/noblink

I now get the message sudo: /etc/network/if-up.d/noblink: command not found

Please help - thank you!

Have you tried 
> sudo chmod +x /etc/network/if-up.d/noblink
before typing sudo /etc/network/if-up.d/noblink?

---

### Post by xg7 on 2009-03-23
That last command worked perfect!  I have no idea what chmod is or does, but it sure worked - sweet.  

Thanks again

---

### Post by xg7 on 2009-03-23
> **irv said:**
> Go to the menu: System> Administration> Login> Security tab. Put a check in the auto login. **You may have to put your script in a public place for all to run it. and make sure you make it Excusable**.

Not sure what this part is referring to.  Thanks!

---

### Post by acreech on 2009-03-23
the chmod +x command changed the mode of the file to executable I believe. Also you can create a folder named "bin" to put your scripts in. Put the folder at /home/bin  If you put your scripts in here then you don't have to type the full path each time. I have a script named "rename.sh". It is at /home/bin/rename.sh, I can execute it by typing "rename.sh" also because I put in the bin folder and not the etc folder, I don't have to use sudo rename.sh......

---

### Post by irv on 2009-03-23
If you want to learn scripting in Linux do a search on the Internet and there are many sites that will teach you all about scripting.
here are just two that I used.

[http://linuxcommand.org/]("http://linuxcommand.org/")
[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")

Irv

---

### Post by acreech on 2009-03-23
> **irv said:**
> If you want to learn scripting in Linux do a search on the Internet and there are many sites that will teach you all about scripting.
here are just two that I used.

[http://linuxcommand.org/]("http://linuxcommand.org/")
[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")

Irv

Thanks the the links. I have only picked up a few commands from the people on the forums trying to help me out. these sites looks like they would be very helpful.

---

### Post by xg7 on 2009-03-23
> **irv said:**
> If you want to learn scripting in Linux do a search on the Internet and there are many sites that will teach you all about scripting.
here are just two that I used.

[http://linuxcommand.org/]("http://linuxcommand.org/")
[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")

Irv

Thanks.  Just curious, when yo umentioned about putting the script in a public place, you were referring to the original script mentioned in this thread (not anything to do with auto-login), correct?

---

### Post by xg7 on 2009-03-23
I was prompted for my network password - where, when I wasn't doing auto-login, I was never prompted.  What's happened?

---

### Post by Bachstelze on 2009-03-23
You need to make the script executable:

```
sudo chmod +x /etc/network/if-up.d/noblink
```

---

### Post by xg7 on 2009-03-23
[QUOTE=HymnToLife;6944790]You need to make the script executable:

```
sudo chmod +x /etc/network/if-up.d/noblink
```[/QUOTE

Thank you.  I got this to work yesterday after that suggestion was made.  Now I'm wondering why I had to re-enter my wifi code when I enabled auto0login.  When I disabled auto-login, I was not prompted for a wifi code.

Any help greatly appreciated.

Thanks :)

---

### Post by irv on 2009-03-23
> **xg7 said:**
> Thanks.  Just curious, when yo umentioned about putting the script in a public place, you were referring to the original script mentioned in this thread (not anything to do with auto-login), correct?

Yes, nothing to do with auto login. That was a separate issue.

---

### Post by irv on 2009-03-23
> **xg7 said:**
> I was prompted for my network password - where, when I wasn't doing auto-login, I was never prompted.  What's happened?

If you have a check in Auto Login, it shouldn't be asking for a password. If you have others logging in you should not have the Auto Login checked. This is just a way to login automatically if you login with the same name all the time. Remember that any one can turn on you pc and there will be logged in.

---

### Post by irv on 2009-03-23
> **xg7 said:**
> [QUOTE=HymnToLife;6944790]You need to make the script executable:

```
sudo chmod +x /etc/network/if-up.d/noblink
```[/QUOTE

Thank you.  I got this to work yesterday after that suggestion was made.  Now I'm wondering why I had to re-enter my wifi code when I enabled auto0login.  When I disabled auto-login, I was not prompted for a wifi code.

Any help greatly appreciated.

Thanks :)
Are you talking about you security code from your router? Setting auto login has nothing to do with router security. I don't understand why that should come up?

---

### Post by xg7 on 2009-03-23
> **irv said:**
> [QUOTE=xg7;6945062]
Are you talking about you security code from your router? Setting auto login has nothing to do with router security. I don't understand why that should come up?

Yes, with auto-login enabled I am being prompted for my router password (wifi). I disabled auto-login and this didn't happen.

?

---

### Post by irv on 2009-03-24
> **xg7 said:**
> [QUOTE=irv;6946092]

Yes, with auto-login enabled I am being prompted for my router password (wifi). I disabled auto-login and this didn't happen.

?
The reason my setup doesn't ask for a router login is because I don't have a router password setup. I guess I wasn't aware of this happening?

---

