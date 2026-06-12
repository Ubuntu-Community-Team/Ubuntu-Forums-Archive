---
title: "Samba - How to make my shared folder accessible to Windows 10"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by horsebox2 on 2017-02-11
**SOLVED: **See last post for solution. 

I setup a folder on my Ubuntu PC and need to share it so I can access it on my Windows 10 laptop. So far, the Windows machine can't detect the shared folder. It detects the Ubuntu computer but can't access it. I installed samba, and created the folder ```
/home/horse/switch
```, I set it to a shared folder using nautilus. It has 777 permissions:

[https://i.gyazo.com/89e8af1ad9788378f2e503f4cc849718.png](https://i.gyazo.com/89e8af1ad9788378f2e503f4cc849718.png)

When I set the share up, it didn't add anything to ```
/etc/samba/smb.conf
``` file, so I added this myself:
```
[switch]
path = /home/horse/pass
valid users = horse entheologist
read only = no
browseable = yes
public = yes
writable = yes
comment = Pass between laptop and Ubuntu
```

So after restarting samba with **/etc/init.d/samba restart** when I run **testparm -s **everything looks right:
```


[switch]
    comment = Pass between laptop and Ubuntu
    path = /home/horse/switch
    guest ok = Yes
    read only = No
    valid users = horse entheologist

```


So on the Windows 10 machine, I tried to connect to the share:
[https://i.gyazo.com/c3f6486ea178f43ed420a895115dce14.png](https://i.gyazo.com/c3f6486ea178f43ed420a895115dce14.png)

and it asked me for login details:
[https://i.gyazo.com/8e0645dea8c0a4d6254aaaf6a694d494.png](https://i.gyazo.com/8e0645dea8c0a4d6254aaaf6a694d494.png)

I entered login details which I know are correct for both Ubuntu and for samba, but I got this message:
[https://i.gyazo.com/6382953e0a8d657fd5da11b7a594b2e0.png](https://i.gyazo.com/6382953e0a8d657fd5da11b7a594b2e0.png)

the Windows machine detects the Ubuntu machine:
[https://i.gyazo.com/26d5e408ca6def1438a9cbfef25aff06.png](https://i.gyazo.com/26d5e408ca6def1438a9cbfef25aff06.png)
if I try to go into \\HORSE, it won't let me, but I can get into \\192.168.1.168:
[https://i.gyazo.com/8c98f6f9a8252cdcfa78b1820ec91132.png](https://i.gyazo.com/8c98f6f9a8252cdcfa78b1820ec91132.png)

I just can't actually get into the shared folder, it keeps asking me for credentials, but when I enter them it tells me I have no permission. 

I ran this:
```
sudo smbpasswd -a horse
```
and set the password. horse is the username on the Windows machine too, so to avoid any possible clashes I added a new user called entheologist and ran smbpasswd on that user too. In the smb.conf file, these two parameters are set:

```
workgroup = WORKGROUP
wins support = yes

```

I ran ```
sudo ufw disable
``` just to make sure the Ubuntu firewall isn't interfering. But I can't see the shared folder on the Windows machine. How would I go about diagnosing what the specific problem is?

---

### Post by Morbius1 on 2017-02-11
There is one minor thing:
> I set it to a shared folder using nautilus.
> It doesn't automatically add anything to the /etc/samba/smb.conf  file, so I added this myself:
[QUOTE][switch]
path = /home/horse/pass
valid users = horse entheologist
read only = no
browseable = yes
public = yes
writable = yes
comment = Pass between laptop and Ubuntu 
[/QUOTE]
You just shared it twice. Nautilus ( nautilus-share ) doesn't create share definitions in smb.conf. It sets them in /var/lib/samba/usershares. Also there is no such thing as "valid users" in nautilus-share so you have two shares of the same folder configured differently. Run this command to see how your nautilus shares are set:
```
net usershare info --long
```
This "double sharing" causes weird errors sometimes so I'd get rid of one of them.

But the other thing is why are you trying to access \\192.168.1.16\shared in Windows when the share is located at \\192.168.1.16\switch?

---

### Post by horsebox2 on 2017-02-11
Sorry I meant switch, not shared. Anyhow, I ran that command and heres what it outputted:
```
horse@horse:~$ net usershare info --long
[switch]
path=/home/horse/switch
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/pass is not a well formed usershare file.
info_fn: Error was Path is not a directory.


```

pass is what I called the share originally but I changed it. I don't know which is a better way to do this. If the nautilus way actually works then I'd use that way since I prefer having shares stored as their own files like that.


EDIT: I deleted /**var/lib/samba/usershares/switch**, but I'm still getting the same permissions problem. Its definitely detecting the shared folder, it just won't let me in. Heres what smbtree outputs:

```
horse@horse:~$ smbtree
Enter horse's password: 
WORKGROUP
    \\LAPTOP-72BLDDCI        
    \\HORSE                  horse server (Samba, Ubuntu)
        \\HORSE\IPC$               IPC Service (horse server (Samba, Ubuntu))
        \\HORSE\switch             Pass between laptop and Ubuntu
        \\HORSE\print$             Printer Drivers


```

but smbstatus outputs nothing:

[IMG]https://i.gyazo.com/54580c2e554763298e674cf2d6e848cd.png[/IMG]

smbclient detects the share:

```
horse@horse:~$ smbclient -L localhost
WARNING: The "syslog" option is deprecated
Enter horse's password: 
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.4.5-Ubuntu]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    switch          Disk      Pass between laptop and Ubuntu
    IPC$            IPC       IPC Service (horse server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.4.5-Ubuntu]

    Server               Comment
    ---------            -------
    HORSE                horse server (Samba, Ubuntu)
    LAPTOP-72BLDDCI      

    Workgroup            Master
    ---------            -------
    WORKGROUP            HORSE


```

I have no idea why its telling me OS=[Windows 6.1]. It seems I was closer to getting this working using the nautilus method.

---

### Post by Morbius1 on 2017-02-11
There's the problem I was describing above. You have two shares with the same name of the same folder:

This one allows guest access:
> 
[switch]
path=/home/horse/switch
comment=
usershare_acl=Everyone:F,
guest_ok=y 

THis one only allows two users access:
> [switch]
path = /home/horse/pass
valid users = horse entheologist
read only = no
browseable = yes
public = yes
writable = yes
comment = Pass between laptop and Ubuntu
Which one Samba will obey is anyone's guess.

On the surface either one will work on it's own - unless you encrypted your home directory then only the one will smb.conf will work - and only if "horse" accesses it from Windows.

[COLOR=#0000cd]**EDIT**: Wait. I missed something. There is no such thing as /home/horse/pass. So that share definition will get you nowhere.[/COLOR]

---

### Post by ajgreeny on 2017-02-11
Please do not use large images inline in your posts.

Users with slow or dial up connections (yes such things are quite common or even normal in some places) may give up waiting for the post to load.

Use thumbnails with the paperclip icon in the toolbar; you will need to use the "Reply to Thread" button or "Go Advanced" if using "Quick reply".

---

### Post by horsebox2 on 2017-02-11
> **Morbius1 said:**
> There's the problem I was describing above. You have two shares with the same name of the same folder:

This one allows guest access:


THis one only allows two users access:

Which one Samba will obey is anyone's guess.

On the surface either one will work on it's own - unless you encrypted your home directory then only the one will smb.conf will work - and only if "horse" accesses it from Windows.

[COLOR=#0000cd]**EDIT**: Wait. I missed something. There is no such thing as /home/horse/pass. So that share definition will get you nowhere.[/COLOR]

I deleted both shares from the usershares folder, so that I am just using whats in the smb.conf file. Still having the same problem. I added a new share with slightly different settings to see if this will work:
```
[share_test]
interfaces = 127.0.0.0/8 192.168.1.0/24
bind interfaces only = yes
map to guest = Bad User

   path = /home/horse/share_test
   writable = yes
   guest ok = yes
   guest only = yes
   create mode = 0777
   directory mode = 0777
   share modes = yes
```

Windows detects the shared folder, but its still telling me permission denied. Neither of the shares are asking me for login credentials anymore, its like its cached somewhere. Thats obviously a problem since share_test is set to guest only so it doesn't allow logged in users.

Running smbstatus with no parameters gives me weird results:```
horse@horse:~$ sudo smbstatus

Samba version 4.4.5-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
3767    entheologist entheologist 192.168.1.2 (ipv4:192.168.1.2:24592)      SMB3_11           -                    partial(AES-128-CMAC)

Service      pid     Machine       Connected at                     Encryption   Signing     
---------------------------------------------------------------------------------------------
share_test   3767    192.168.1.2   Sat Feb 11 20:50:03 2017 GMT     -            -           

No locked files


```

Whats weird is:
1.) Only the new share (share_test) is showing up. 
2.) Its saying that the machine that its on is 192.168.1.2. 192.168.1.2 is the IP of the Windows machine. Also the only user its listing is entheologist, I don't know what thats all about. I'm confused about all this, especially about how its listing the Windows machines IP as the machine.

---

### Post by Morbius1 on 2017-02-11
Change this:
> [share_test]
interfaces = 127.0.0.0/8 192.168.1.0/24
bind interfaces only = yes
map to guest = Bad User

   path = /home/horse/share_test
   writable = yes
   guest ok = yes
   guest only = yes
   create mode = 0777
   directory mode = 0777
   share modes = yes
To this:
> [share_test]
path = /home/horse/share_test
   writable = yes
   guest ok = yes
force user = horse
Then restart smbd:
```
sudo service smbd restart
```

---

### Post by horsebox2 on 2017-02-11
> **Morbius1 said:**
> Change this:

To this:

Then restart smbd:
```
sudo service smbd restart
```

I tried what you said. When I tried to access shared_test on Windows, it asked me for login credentials this time, so I tried to login as horse (tried both the samba password and the Ubuntu password), but got the same old permissions problem. I updated my previous post to add some weird diagnostic details that are showing up.

---

### Post by Morbius1 on 2017-02-11
It's a guest accessible share so you shouldn't receive a credentials prompt in Windows.

Post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by horsebox2 on 2017-02-11
> **Morbius1 said:**
> It's a guest accessible share so you shouldn't receive a credentials prompt in Windows.

Post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

I know, there is some kind of caching thing happening. After restarting Windows, its now working but I'll get to that in a minute. Heres what testparm -s says:
```
[switch]
    comment = Pass between laptop and Ubuntu
    path = /home/horse/switch
    read only = No
    valid users = horse entheologist


[share_test]
    path = /home/horse/share_test
    force user = horse
    guest ok = Yes
    read only = No


```

and 
```
net usershare info --long
```

outputs nothing. I was going to ask about this, this net command doesn't seem to work at all, at least not for interacting with samba. Running:
```
net conf setparm parameter value
```
doesn't change anything in the smb.conf file. Running **net usershare list**, lists nothing. This is bothering me because I want to eventually setup a script that will setup shares automatically, so this net tool would be very useful for that.

---

### Post by horsebox2 on 2017-02-11
**SOLVED:**

The problem is finally resolved. More or less anyway. I restarted the Windows machine and noticed it didn't automatically discover my Ubuntu machine but I clicked Run, and pointed it to **\\192.168.1.16**, it prompted me to provide login credentials, I put in horse as the username and used the samba password for that user and it worked, it let me into the folder that lists the shares for the Ubuntu machine. Additionally, now I can get into those shares, theres no more login prompts. So it seems like when you login to a network device once with Windows, it caches the login details and then uses them for every share you try to access. Its a pain in the ass. That shouldn't have caused the issues I was having though. 

EDIT: Wait, out of 3 shares I made, its only letting me access 2 of them. Heres the parameters:

```
[switch]
    comment = Pass between laptop and Ubuntu
    path = /home/horse/switch
    read only = No
    valid users = horse entheologist


[share_test]
    path = /home/horse/share_test
    create mask = 0777
    directory mask = 0777
    guest ok = Yes
    guest only = Yes
    read only = No


[share_test2]
    path = /home/horse/share_test2
    force user = horse
    guest ok = Yes
    read only = No


```

The one it won't let me access is **share_test**. I'm pretty sure its due to this caching thing. share_test is set to guest only = Yes, so Windows is obviously automatically trying to access it with the login credentials I gave it when I connected to the Ubuntu network device.

EDIT: Remove guest only = Yes from the share_test entry resolved the issue with it, I can access it now form the Windows machine.

---

### Post by Morbius1 on 2017-02-11
> **horsebox2 said:**
> I know, there is some kind of caching thing happening. After restarting Windows, its now working but I'll get to that in a minute. Heres what testparm -s says:
```
[switch]
    comment = Pass between laptop and Ubuntu
    path = /home/horse/switch
    read only = No
    valid users = horse entheologist


[share_test]
    path = /home/horse/share_test
    force user = horse
    guest ok = Yes
    read only = No


```
If that is the only thing testparm -s outputs then it's a miracle samba works at all. When someone asks for the output of a command it's best to output all of it.
> Running **net usershare list**, lists nothing. This is  bothering me because I want to eventually setup a script that will setup  shares automatically, so this net tool would be very useful for that.
THere's nothing to list because you have no usershares as demonstrated by this:
> and 
```
net usershare info --long
```

outputs nothing.
> This is bothering me because I want to eventually setup a script that will setup shares automatically, so this net tool would be very useful for that.
You can create a samba share from the command line using usershare.

---

