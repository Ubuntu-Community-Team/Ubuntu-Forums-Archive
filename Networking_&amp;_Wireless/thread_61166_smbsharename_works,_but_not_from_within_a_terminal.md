---
title: "smb://sharename/ works, but not from within a terminal"
date: 2005-08-30
forum: Networking &amp; Wireless
---

### Post by borris on 2005-08-30
Hi all,

I have what I think is a weird problem.  I followed the directions in the ubuntuguide.org to see a windows network computer on a work LAN... it works fine:
Applications-> Run Application -> smb://computer/share 
I then get prompted for a username, domain and password, which I enter, and presto, access to that computer.

My problem is that I want to have access from the terminal so that I can run commands (like backing up using rsync) to that computer from my Ubuntu computer.  So I tried mounting it...

So I follow the ubuntuguide.org again:
sudo mkdir /media/sharename
sudo mount //samecomputer/sameshare /media/sharename/ -o username=same.myusername,password=same.mypassword

Then I get:
9079: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

Any thoughts?

---

### Post by ebrowne on 2005-08-30
Hey, 
It's been a while since I've done this but I think you need  to add the -t option

ie sudo mount -t smbfs //samecomputer/sameshare /media/sharename/ -o username=same.myusername,password=same.mypassword

hope this helps

Oh you may want to sudo apt-get install smbfs as well

I seem to recall having to use smbmount

---

### Post by s_p_a_r_k_y on 2005-08-31
what happens when you do this

smbclient -L windowsbox -U usernameOnWindows

it will prompt for a password but will show the shares. Share names are case sensitive

---

### Post by borris on 2005-08-31
Thanks S_P_A_R_K_Y and ebrowne, but those didn't work.

When I did this:
smbclient -L windowsbox -U usernameOnWindows

I got:
session setup failed: NT_STATUST_LOGON_FAILURE

When I did this:
sudo mount -t smbfs //samecomputer/sameshare /media/sharename/ -o username=same.myusername,password=same.mypassword

I got:
8864: session setup failed: ERRDOS -ERRnoaccess (Access denied.)
SMB connection failed

In case this helps, where you write "windowsbox", I have tried:
windowsboxName
windowsboxIPaddress
//windowsboxName
//windowsboxIPaddress
//windowsboxIPaddress/sharename

Again, I can ping it using just its name, and it is there.  

Any more ideas?

---

### Post by ebrowne on 2005-08-31
Hey,
You should see this with smbclient

smbclient -L localhost -U ebrowne
Password: 
Domain=[DEV] OS=[Unix] Server=[Samba 3.0.10-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (dev server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (dev server (Samba, Ubuntu))
        darryl          Disk      Home Directories
Domain=[DEV] OS=[Unix] Server=[Samba 3.0.10-Ubuntu]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        MSHOME               DEV
        WORKGROUP            DARRYL-DTL

The password I used is the password created by smbpasswd for that user.

I get  NT_STATUS_LOGON_FAILURE
 when I type an incorrect password.

smbmount list :
mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test
as the mount command to use I believe if you leave password out it will prompt for it.

---

### Post by borris on 2005-08-31
Hi ebrowne,

If I write this:
smbclient -L localhost -U MyUserNameOnThisComputer

I get:
Password:
session setup failed: NT_STATUS_LOGON_FAILURE

I know the password is correct, because I am logged on to this computer right now.  I also know it is correct on the other computer (the one I am trying to reach), because I can do:

Applications->Run Applications->smb://Saskatoon/SELES
prompt for password, I type it, and presto, I have access to the other computer.

Again, this would be fine, but I want it mounted, so I can access if from other programs. 

More thoughts?

---

### Post by ebrowne on 2005-08-31
Hey, My first thought would be to reset the password.  using smbpasswd <username>  You getting som kind of authentication error I'm assuming it's locally on the same machine as samba is running?  If not can you try mounting it locally on that machine?  if that works I'd suppect a firewall is causing your problem.

---

### Post by mwigge on 2005-09-01
Hi,

i actually have the same problem...

mount -t smbfs //fileserver/userid$ /mnt/samba/userid -o username=XX,workgroup=XX   does not work..

and places > connect to server >
Service type: Windows share
Server:fileserver
Share:userid$
User Name: Domain\userid

does not work either

but Applications -> run application: smb://fileserver/userid$ 
gives me a login window and everything works...

and i also have no problem connecting via smbclient.. i can list all shareings with smbclient -L fileserver
and i can also connect to my share via smbclient //fileserver/userid$ -W workgroup


bug in ubuntu?

---

### Post by ebrowne on 2005-09-01
This all works for me... I can mount using mount smbmount or from a window box something else isn't configured correctly  I'm using Hoary.

---

### Post by borris on 2005-09-01
It isn't working.

I did the smbpasswd thing, changed my passwd, but it is only for this computer.  I can't see the other computer using any of these suggestions.

Else?

---

### Post by s_p_a_r_k_y on 2005-09-02
borris, let me get a few thingies straight. From nautilus everything is working correct? However the same information isn't working from the mount command? Also when you smbclient -L windowsbox -U WindowsUserName you don't see any shares?

---

### Post by nathan43081 on 2005-09-06
I am having a very similar problem. I can samba mount using smb:://servername/share and then putting in all of my info, but if I try to do a mount -t smbfs -o username=myusername //servername/share /local_dir then I get a loop asking me to reinput my password. When I try to do a smbclient -L servername then I get a list of all of the shares that are on the box. 

Any thoughts as to why we can't manally use mount to do this?

---

### Post by nathan43081 on 2005-09-06
[QUOTE=nathan43081]I am having a very similar problem. I can samba mount using smb:://servername/share and then putting in all of my info, but if I try to do a mount -t smbfs -o username=myusername //servername/share /local_dir then I get a loop asking me to reinput my password. When I try to do a smbclient -L servername then I get a list of all of the shares that are on the box. 

Any thoughts as to why we can't manally use mount to do this?[/QUOTE]
 I finally found a fix to my problem just after posting this. It was to install the package smbfs using apt. I guess if it isn't installed it makes sense for it not to work from the command line.

---

### Post by borris on 2005-09-06
Hi sparky and nathan43081,

Sparky... yes, you are right, when I type smbclient -L WindowsBoxIWantToConnectTo -U MyUserNameIKnowWorksOnThatComputer, I get either:

Connection to saskatoon failed
 
or

session setup failed: NT_STATUS_LOGON_FAILURE

depending on whether I write the short name of the computer, or the whole name of the computer (i.e., name.site.domain.com), in that order.

If I type:
smbclient -L MyLinuxBox -U MyUserName

I get a list of all the shares on my computer.

nathan43081:
I already had smbfs installed, and smbclient, both up to date in the ubuntu apt-get.

It still isn't working.

I've basically given up, unless somebody has a great solution.  I'm getting access to the other computer via rdesktop, then running backup software on the WindowsBox, grabbing the files from my Ubuntu box to back up to the Windows Box.  Very inefficient.  But it is working for now.

Any more thoughts?


Eliot

---

### Post by s_p_a_r_k_y on 2005-09-06
Borris can we see the command you are actually trying, not something with fakenames like WindowsBox and WindowsShare. also the output of smbclient when you get a listing. The names are case sensative I believe. Also you wont be able to list shares via the full DNS path of a computer bc smb looks up only based on netbios (I believe). I am no samba specialist but I have had my experience with it 3+ years and am usually pretty good at getting to the bottom of things. If you wanna do an IRC session or talk on aim that would be fine as well.

---

### Post by mariux on 2005-10-29
It doesnt work here either. I can mount it with no problem in konqueror using smb://vladimir/media but trying to mount it so that i can access it system wide from the commandline doesnt work.

 
mariux@nylon:~/download$ sudo aptitude search smbfs
i smbfs - mount and umount commands for the smbfs (for kernels >= than 2.2.x)

mariux@nylon:~/download$ smbclient -L vladimir -U mariux
Password:
Domain=[VLADIMIR] OS=[Unix] Server=[Samba 3.0.20b]

        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        print$          Disk      Printer Drivers
        MARIUX          Disk      LOL
        media           Disk      medialol
        Unnamed         Printer
        hpprinter       Printer
        IPC$            IPC       IPC Service (vladimir server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (vladimir server (Samba, Ubuntu))
        HP              Printer   Skjera?
Domain=[VLADIMIR] OS=[Unix] Server=[Samba 3.0.20b]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        MSHOME               VLADIMIR

 
mariux@nylon:~/download$ sudo mount -t smbfs -o username=mariux,password=mypass //vladimir/media /mnt/media/
mariux@nylon:~/download$ sudo ls /mnt/media
ls: /mnt/media: Input/output error
 
mariux@nylon:~/download$ sudo smbmount //vladimir/media /mnt/ipod -o username=mariux,password=mypass
mariux@nylon:~/download$ sudo ls /mnt/ipod
ls: /mnt/ipod: Input/output error


The problem is NOT case sensitivity since samba on the server is set to "ignore case" AND i've tried it caps on the client, no difference.

Also, when hitting tab for autocomplete on "/mnt/me" takes forever when having mounted a smbfs in that dir.

---

### Post by mariux on 2005-10-29
I've found a way to fix it! 
 
I read some other posts on the forum and did some experimenting and found a combination that worked. (found here [http://www.ubuntuforums.org/showthre...light=smbmount](http://www.ubuntuforums.org/showthre...light=smbmount) )
 
[b]*working command*
sudo mount.cifs //192.168.0.2/media /mnt/ipod -o user=mariux,pass=mypass
*working command*[/b]
 
Note that even though smbmount and mount -t smbfs finds the host "vladimir" with no problem, this program does not. It does however work perfectly when giving it the ip.
 
 Running smbmount and mount -t smbfs with the ip however does not work, go figure

---

### Post by penvzila on 2005-12-11
I couldn't get mounting of samba shares to work either until I realized one thing: it helps if you actually have smbfs installed!

---

### Post by taurean on 2007-02-24
Oh the frustration !!!!

I search the net hoping to find an answer and finally register here (after using the forums anyway to fix my other nubtype problems!!) and see this thread, thinking VIOLA! Finally...

But to no avail.

I am using dapper, and on my local network I have a simple windows 98 PC with a shared folder so I can easily transfer files between the two.

I can use the "Connect to server" tool to connect to the folder from the GUI, no problem at all. I dont need to bother with passwords or user names. I check the properties of the connection and its simply smb://192.168.1.65/cdrive

Why cannot I do this from a terminal.

There has to be an access point somewhere in the terminal, surely. Or has it all become too much like windows where the GUI overdoes things and renders terminal usability second class??

Thats my problem, after years of windows use, I was stuck in that mindset, but even net use z: //192.168.1.65/cdrive   would have worked over in their camp.

Perhaps some things are just too simple that when seeking an answer we look for harder questions to resolve it.

Any ideas, this thread os pretty old now, so maybe someone can point me to a newer one ? Its the only one I found using search with the terminal access query   ;)

:popcorn:

---

### Post by kpictjl on 2007-07-05
> **taurean said:**
> Perhaps some things are just too simple that when seeking an answer we look for harder questions to resolve it.
I recommend walking through the ubuntuguide.org section on mounting smb shares. [here]("http://http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read").
Looks like it doesn't work for everybody, but it's worked for me on a couple different machines.

---

