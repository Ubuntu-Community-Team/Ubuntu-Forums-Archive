---
title: "Can't access shared files from Vista PC on Ubuntu PC"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by bg1256 on 2008-01-19
Hello all,

Here's my set-up:

Vista laptop PC, Ubuntu Desktop PC.

On my notebook, I set up network sharing and shared some various files. 

From my Ubuntu PC, I can see my Vista laptop and its shared files, and I can move them without problems. Also on my Ubuntu PC, I can see that my desktop is part of the network.

From my Vista laptop, I can see my desktop computer as part of the network, and when I double click it, it asks for a username and password.

Here is where I get stuck. I am assuming that the correct username and password would be the username and password for the Ubuntu PC. However, when I enter that, it says it is incorrect.

Does anyone know how to solve this dilemma?

Sincerely.

---

### Post by carendon71 on 2008-01-19
Did you do smbpasswd?

You have to add yourself as a samba user (and probably your machine as well)

It's funny, I have a Vista Laptop as well & have no problem connecting to my ubuntu server, but it doesn't like to connect with my other machines (XP & Linux) :p
Vista doesn't play nice with older versions of windows.  I have problems with my vista laptop even talking to my XP machines, let alone my linux ones!

---

### Post by bg1256 on 2008-01-20
Hmmm... can't seem to figure out how to do that.

At least, I do'nt see it in the GUI

---

### Post by rosegarden78 on 2008-01-20
If Microsoft faces class-action lawsuit by Intel, Sun and the EU for withholding formatting information about Word documents, that competitors cannot make compatible products such as OpenOffice, why do you think that Vista is any less secret or complicated than XP?   If programs are still not compatible with XP due to Draconian secrecy of MS file formats, how then is Vista is going to be compatible?  Perhaps Microsoft doesn't mind losing another $750 class-action lawsuit.

---

### Post by bg1256 on 2008-01-21
Well, thanks for your rant...

Any ideas that would help me get this working, though?

---

### Post by BrentC on 2008-01-21
> **bg1256 said:**
> Well, thanks for your rant...

Any ideas that would help me get this working, though?

Just went through this today myself...my guide isn't going to be perfect, but it should get you started and hopefully the veteran members can add onto what I say and possibly fix my permissions problem.

Do you even have SAMBA installed? Not sure what version of Ubuntu you're running, so not sure if it's installed or not. Check, if it's not installed, do a:
```
sudo apt-get install samba
```
After SAMBA is installed, run a:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
This will make a backup of your smb.conf. Then run the following:
```
sudo nano /etc/samba/smb.conf
```
Can use whatever your favorite text editor is if you don't like nano. Comment out everything that isn't commented-out already and then add the following to your smb.conf:
```
 [global]
# Change the value of "workgroup =" to whatever your Window's workgroup is
        workgroup = MSHOME
        server string = Samba Server
        security = user
        encrypt passwords = Yes
        log file = /var/log/samba/%m.log
        max log size = 0
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        os level = 65
        preferred master = True
        domain master = No
        dns proxy = No
        wins support = Yes
        printing = lprng

[data]
    comment = User's share
# "path =" is the folder you wish to share with your Windows client. /home/samba is just an 
example
    path = /home/samba
    public = yes
    writable = yes
    browsable = yes
    create mask = 0774
# You will be replacing the value "user" in the line "valid users =" with the user name you're about 
to create in a minute
    valid users = user
```
Sae your smb.confand then run:
```
sudo useradd -c YOURUSERNAMEHERE
sudo smbpassword -a USERNAMEYOUCHOSEABOVEHERE
```
This should ask you to enter a password and then create a user. Make sure you edit your smb.conf with the user you just created. 

Now this is where I ran into a problem; My Windows client cannot view, write, or do anything to the share we told SAMBA to associate to our user with unless the permissions are set to 777. So, as a temporary solution I did the following(ONLY DO THIS IF YOU ARE HAVING PERMISSION PROBLEMS AFTER SETTING UP THE SAMBA SERVER!):
```
sudo chmod 777 /home/samba (or whatever you set the value "path =" to)
```
**NOTE:** This is not a good thing to do. I would suggest waiting for someone else to explain how to access your shared folder with different permissions. I couldn't figure it out and setting permissions to 777 was the ONLY way I could read and write on my Windows client to my shared SAMBA directory.

Now lets make sure everything works:
```
cd /etc/samba
sudo testparm -s smb.conf
```
If everything looks alright then:
```
sudo /etc/init.d/samba restart
```
Your SAMBA server should be running now. Goto your Windows client and Start-Run, \\Samba\data (\\Samba\data\ since we named our share "data" earlier, you can name it anything you want though). This should bring up a login prompt. Enter the username and password you made earlier and if all went well, you should now be able to do basic file sharing between your linux box and Windows client.

Hope this helps and I am praying we get some SAMBA vets in here to help with the permissions problems. ;)

---

### Post by jonandrews on 2008-01-21
Have a look at my step-by-step Windows / Unbuntu networking guide. It was written around XP, but I've tried it with Vista with no problems

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by rosegarden78 on 2008-01-26
Do you mean networking or just access?  Cuz just read write you need an EXT2 shareware program from Sourceforce if you want to access Ubuntu drive in Windows.  Sorry I can't find the SourceForge address right now.  If you wanna access XP in Ubuntu, GG 7.10 has NTFS support built in.  Otherwise you may need to use ntfs-3g or ntfs-fuse to mount Windows in Ubuntu.

---

### Post by bg1256 on 2008-01-26
Thanks, al,l for your help! I'm sure I'll find something here to sort out my problem.

---

### Post by tekguy on 2008-01-26
> **bg1256 said:**
> Hello all,

Here's my set-up:

Vista laptop PC, Ubuntu Desktop PC.

On my notebook, I set up network sharing and shared some various files. 

From my Ubuntu PC, I can see my Vista laptop and its shared files, and I can move them without problems. Also on my Ubuntu PC, I can see that my desktop is part of the network.

From my Vista laptop, I can see my desktop computer as part of the network, and when I double click it, it asks for a username and password.

Here is where I get stuck. I am assuming that the correct username and password would be the username and password for the Ubuntu PC. However, when I enter that, it says it is incorrect.

Does anyone know how to solve this dilemma?

Sincerely.

All you need to do is this:

Open up a terminal window and type the follow:
```
sudo smbpasswd -a LOGIN_USERNAME 
```

Where LOGIN_USERNAME is the user name you usually log into the ubuntu box with.

You will be prompted to set a password. Since you said you already shared on the Ubuntu box I know you have samba installed.

---

### Post by ockron on 2008-04-07
Tekguy ...

Thank you so much for the advice.
I know I did not start this tread, but I have been battling for days!!!

I can now use the shared folder!!!

Do you know how to share a printer?

---

### Post by Eiríkr on 2008-04-07
Hey there BrentC --

Going over your template smb.conf file, I noted the following:

> **BrentC said:**
> ```
[global]
        ...
        printing = lprng
```

This option is *only* useful within a printer share definition, and does not belong in the [global] section.  Have a look at [the relevant smb.conf man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTING").  

> **BrentC said:**
> ```
[data]
    browsable = yes
    ...
    public = yes
    valid users = user
```

The [browsable]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#BROWSEABLE") value is already the default, making this line redundant and therefore removable.  The latter line has a number of dependencies, and will likely cause unexpected problems as the conf file is currently set up.  The [public]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PUBLIC") option is the same as [guest ok]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTOK"), and it means that any connection attempt to this share that is not listed in the [valid users]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VALIDUSERS") line will use the [guest account]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT").  Since your conf file does not specify this option in the [global] section, the guest account will default to the "nobody" account.  This account is generally very restricted, and may well not have any of the expected filesystem permissions on the shared directory.  Looking over forum posts, it seems to me that forgetting to set the "guest account" option is probably the single most common error in setting up Samba guest access.

Another dependency for guest access is the [map to guest]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPTOGUEST") [global] option.  As noted in the relevant man page section:
> Note that this parameter is needed to set up "Guest" share services when using *[FONT="Courier New"]security[/FONT]* modes other than share and server. This is because in these modes the name of the resource being requested is *not* sent to the server until after the server has successfully authenticated the client so the server cannot make authentication decisions at the correct time (connection to the share) for "Guest" shares. 
I think "Bad User" is the best value for this option for simple guest sharing setups.  

----------

Hope this helps,

Eiríkr

---

