---
title: "SAmba PDC - Roaming Profile &amp;&amp; Folder redirection problem"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by ikus060 on 2007-06-29
Hi,

I need help to fix a problem with Samba as PDC and Folder redirection on a Roaming Profile. I know it's not the best place to post this, but I don't know any better place. So if you have suggestion, tell me.

Here my problem :

I'm in a testing environement with a Samba server setup as a PDC with some share (netlogon, profiles) to support roaming profile. My "smb.conf" file contain the good configuration parameters for "logon path" and "logon home" etc ..

For my roaming profile, I setup a Folder redirection using the 
"HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders" registery key. I modify the value of AppData, Cookies, Desktop, Favorites, My Pictures, Personal. Every folder are redirect to the network share with %LOGONSERVER% and %USERNAME% variable. There is no problem with the redirection, when I connect every thing are correctly redirect.

For example, if I create a file named "textfile.txt" on my desktop, I see it on the shared folder. (I do a "ls" command with ssh directly on the server to be sure). I can add, remove, edit file on the desktop and every thing are OK.

The problem come when I logout The window client do some sort of synchronization of a local folder with the shared folder. For example, C:\Documents and Seetings\admin\Desktop\ with \\MyServer\profiles\admin\Desktop. I fact, it's not a synchronization, it's just delete the shared folder and replace it by the content of the local folder. The result is that every modification done on the desktop (that are redirected) are lost at the logout.

It's a very annoying problem that I can't solve by my self. I search everywhere without any tips.

I try some config with "ExcludeProfileDirs" registry key without success. It's possible that I don't use it correctly.

Thank for you help and comment.


My smb.conf file :
```

[global]
        dos charset = 850
        unix charset = UTF8
        workgroup = ENTREPRISESMD
        server string = Samba server
        passdb backend = ldapsam:ldap://127.0.0.1/
        time server = Yes
        deadtime = 15
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        add user script = /usr/sbin/smbldap-useradd -m "%u"
        delete user script = /usr/sbin/smbldap-userdel "%u"
        add group script = /usr/sbin/smbldap-groupadd -p "%g"
        delete group script = /usr/sbin/smbldap-groupdel "%g"
        add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
        delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
        set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
        add machine script = /usr/sbin/smbldap-useradd -w "%u"
        logon script = login.bat OR %U.bat
        logon path = \\%L\PROFILES\%U
        logon drive = h:
        logon home = \\%L\PROFILES\%U
        domain logons = Yes
        os level = 40
        domain master = Yes
        dns proxy = No
        wins support = Yes
        ldap admin dn = cn=admin,dc=entreprisesmd,dc=homeip,dc=net
        ldap delete dn = Yes
        ldap group suffix = ou=Group
        ldap idmap suffix = ou=People
        ldap machine suffix = ou=Computers
        ldap passwd sync = Yes
        ldap suffix = dc=entreprisesmd,dc=homeip,dc=net
        ldap user suffix = ou=People
        winbind use default domain = Yes
        inherit permissions = Yes
        inherit acls = Yes
        inherit owner = Yes
        case sensitive = No
        hide files = /desktop.ini/ntuser.ini/NTUSER.*/
        msdfs root = Yes

[netlogon]
        comment = Network Logon Service
        path = /data/usersdata/netlogon
        read only = No
        browseable = No

[PROFILES]
        comment = User profiles
        path = /data/usersdata/profiles
        read only = No
        create mask = 0600
        directory mask = 0700
        inherit permissions = No
        inherit acls = No
        inherit owner = No
        profile acls = Yes
        browseable = No
        csc policy = disable

```

---

### Post by armnpsycho on 2007-06-30
ikus,

DId you set up the folder redirection in the GPO as well?

---

### Post by ikus060 on 2007-06-30
Hi armnpsycho,
First I want to thank you for your reply. 

I'm really surprise that you talking about GPO because I thought that I don't have to play with this if i'm using the registry key. So I take a look in the Group Policy tool (gpedit.msc) to setup de folder redirection. I Google "Folder redirection" and find that with can modify the value in User Configuration/Windows Settings/Folder Redirection.

It's funny because I don't have this item in the Group Policy tool (see attachment). So, I Google it and found this [http://support.microsoft.com/kb/888254](http://support.microsoft.com/kb/888254). It's tell me to install some "fix" to enable the Folder redirection option. Before installing this "fix", I just want to be sure that it's really important to install and that I need this.

Is it possible that I need to install something, like an extention to get the folder redirection in the GPO ?? I seen that on some web site of MS.

Also, I just want to make something clear, when I edit the policy, I do this on the working station. Not like AD on the global network.

---

### Post by Gallows on 2007-06-30
It seems to me as if you haven't setup full folder redirection but are using roaming profiles.  When using roaming profiles any changes made directly to the network storage area will be lost if the local copy of the profile is different. 

[This]("http://blogs.msdn.com/oldnewthing/archive/2005/06/30/434209.aspx") MSDN blog has a good explanation of the issues surround roaming profiles and why in a corporate environment you should avoid then at all costs.

---

### Post by ikus060 on 2007-06-30
In fact, when I logout Windows do some synchronization with the local directory (c:\Document and setting\admin\desktop) and the remote folder (\\MyServer\profiles\admin\desktop\) .

In a log file for user environment (c:\windows\debug\usermode\userenv.txt) it's clear that windows just remove the file I create :
```
USERENV(25c.260) 20:36:52:752 SyncItems: removing <E:\admin\Desktop\New Text Document.txt>
```

---

### Post by ikus060 on 2007-06-30
I read the blog. It's doesn't encourage me to continue my testing with roaming profile.  

There is any replacement technology that provide the benefit of roaming and the stability of local profile ??

The main feature I need is to execute login script (to map network location, execute an app (home made app)) and to redirect folder Desktop, MyDocs, Favorites, etc to a network share.


Does every body have bad experience with roam profile ??

---

