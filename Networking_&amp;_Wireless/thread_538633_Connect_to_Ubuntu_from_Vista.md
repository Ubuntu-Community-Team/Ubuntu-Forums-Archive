---
title: "Connect to Ubuntu from Vista?"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Tom Stanley on 2007-08-30
Hi everyone,

Great forum! I'm having trouble with Ubuntu. I want to connect to Ubuntu from Vista, but when I type in the PC Name, Vista asks for my username and password, I enter them, but it says they are incorrect?

Am I doing something wrong?

Thanks,

Tom :)

---

### Post by cagey cretin on 2007-08-30
What service are you trying to connect to on Ubuntu, and how are you trying to connect?

---

### Post by cagey cretin on 2007-08-30
And, the username and password you enter are the username/password for Ubuntu, right?

---

### Post by Tom Stanley on 2007-08-30
Hi everyone,

Yep, the user name/password are correct for the Ubuntu machine, and I'm just using Window's built in networking tools (\\nameofpc) to cOnnect to the computer. :)

---

### Post by cagey cretin on 2007-08-30
> **Tom Stanley said:**
> Hi everyone,

Yep, the user name/password are correct for the Ubuntu machine, and I'm just using Window's built in networking tools (\\nameofpc) to cOnnect to the computer. :)

Have you set up Samba shares in Ubuntu? It's just like Windows in that you have to have a share that you share that someone can connect to. I don't use Samba myself. I connect via ssh, http, etc.I bet there is an Samba tutorial here somewhere...

---

### Post by Tom Stanley on 2007-08-30
HI again,

Yep, they are set up, I just cannot connect? The computer can be seen in the network view, but I cannot connect? Do I need some extra software installed?

Thanks

Tom :)

---

### Post by cagey cretin on 2007-08-30
> **Tom Stanley said:**
> HI again,

Yep, they are set up, I just cannot connect? The computer can be seen in the network view, but I cannot connect? Do I need some extra software installed?

Thanks

Tom :)

I don't use Samba, so I can't say what software you have to install, but you must have a service available (in this case Samba), and you must have ports that are open for this service to be connected to. Check out this page for Samba ports that you must allow incoming traffic onto your Samba server (I am sure there is one here as well):
[http://download1.swsoft.com/Plesk/Plesk8.2/Doc/plesk-win-pmm-guide/21821.htm](http://download1.swsoft.com/Plesk/Plesk8.2/Doc/plesk-win-pmm-guide/21821.htm)

As to the second, can you confirm that Samba is running?

#netstat -tap (maybe sudo netstat -tap)

The above command should show what services are listening and on what ports. 

nmap -p1-1024 <ip.address.of.server> should show what ports are available.

---

### Post by Benedolt on 2007-09-05
Hey Tom.
You can work around this problem by editing a value in your samba configuration file. (Sorry, don't know about the GUI ay to do it.)
Fire up a terminal, and type 'sudo nano /etc/samba/smb.conf', now search ('Strg+W' in nano) for this line:```
security "user"
``` and change it into ```
security "share"
```
Save with Strg+O and quit using Strg+X. Then reboot or simply reload samba using 'sudo /etc/init.d/samba restart'

It should work now...

---

### Post by yudiwashere on 2007-09-07
hi, 
i also faced same thing try to connect from xp to feisty. instead of using the xp desktop, i used feisty desktop to connect to xp desktop. i use 1 folder in xp to share my files (all access) so i can transfer files from feisty to xp.
to view the xp shared folder click Places > Network > Windows Network > workgroup (this may differ from your windows setting). then you can view the windows connected pc(s). select the pc that you want to make the connection.
I hope this will help you. well, it does for me for now. but, i'm still trying to connect via winscp and putty from xp to feisty.

yay! i found the solution for my problem. 
> sudo apt-get install ssh
it seems that feisty did not install ssh service for me

---

### Post by scxtt on 2007-09-07
in ubuntu, you have to allow a user access to samba shares ... assuming you have samba installed and running, you need to do the following on your ubuntu box:

sudo smbpasswd -a $USER

then enter a password, this is effectively what windows is prompting you for ...

---

### Post by bagjadl on 2007-09-10
> **Benedolt said:**
> Hey Tom.
You can work around this problem by editing a value in your samba configuration file. (Sorry, don't know about the GUI ay to do it.)
Fire up a terminal, and type 'sudo nano /etc/samba/smb.conf', now search ('Strg+W' in nano) for this line:```
security "user"
``` and change it into ```
security "share"
```
Save with Strg+O and quit using Strg+X. Then reboot or simply reload samba using 'sudo /etc/init.d/samba restart'

It should work now...

That worked a treat for me, saved a lot of hair pulling thanks.  Think I'll have to stumble this.

---

### Post by Tom Stanley on 2007-10-19
Hi,

Thanks for the info, I'll try it soon. Sorry I haven't replied, family issues!!

Tom :)

---

### Post by beastly on 2007-10-19
One thing to beware of with Vista is that it forces NTLMv2 authentication by default. The result is that unless your Samba share is set up with NTLMv2, it will simply give an authentication failure which implies that the login is incorrect.

The solution is to add the following line to the [global] section of /etc/samba/smb.conf

client NTLMv2 auth = yes

Save the file then restart Samba - /etc/init.d/samba restart

Another solution is to run secpol.msc from the run box within Vista, click on Security Options under Local Policies on the left hand side. There is an entry called "Network security: LAN Manager authentication level" which will be set to "Send NTLMv2 response only" by default. You can lower this to "Send NTLM response only" which should resolve this issue. The preferred option is to modify the Samba server settings if possible though.

---

### Post by Tom Stanley on 2007-10-20
Hi,

It still won't work. I've tried both of the above, and it's still not working?

Anyone got any ideas?

Thanks,

Tom :)

---

