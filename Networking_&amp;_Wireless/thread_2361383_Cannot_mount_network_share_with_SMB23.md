---
title: "Cannot mount network share with SMB2/3"
date: 2017-05-15
forum: Networking &amp; Wireless
---

### Post by bak&#305;r on 2017-05-15
Hi all,

We have a Windows server at our institution on which people put their data. Due to the recent wave of ransomware attacks, smbv1 had to be blocked. Now the problem is that machines running Ubuntu and derivatives cannot connect to it anymore, which they apparently were accessing through smb1.

The standard protocol now gets refused as it should be:
```
smbclient  <URL> -U <username> -W WIN
protocol negotiation failed: NT_STATUS_CONNECTION_RESET
```


We could changing the protocol to make smbclient connect successfully:
```
smbclient  <URL> -U <username> -m SMB3 -W WIN
Domain=[WIN] OS=[] Server=[]
smb: \>
```


But I cannot mount the drive through Nemo GUI, nor using to command line with cifs.
```
sudo mount -t cifs -o username=<username>,domain=WIN,vers=2.0 <URL> ./server
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```


Similarly for v2.1 or 3. The kernels are > 4.2. Any ideas what might be causing the issue or how to fix this problem would be appreciated.

Thanks.

---

### Post by bab1 on 2017-05-16
I believe your problem stems from a setting in the smb.conf file and an incompatibility with SMB2 and SMB3.  By default the Unix Extension parameter is set to 'yes'..   Unfortunately this only works for SMB1.  Simply put; Unix Extensions have not been developed for SMB2 or SMB3 yet.  

My suggestion is to set the following in the [Global] section of the smb.conf file```
unix extensions = No
```
Remember to restart the smbd daemon before continuing on.  This should no allow you to use SMB2.  You might have symlink or hardlink problems if your users use those features, since that is what Unix Extensions translate Linux file system attributes from NTFS to EXT4 (or some such).

---

### Post by bak&#305;r on 2017-05-16
Thank you, I tried adding but it did not solve the problem. Still the same problem happens with commands, Nemo cannot connect.

On the other hand, I found a work around in the mean time. One needs to specify as target directory subdirectory to which user has access rights, followed by "/". It previously managed to list the parent directory.

My ideas:
Either there is a problem with the smb I have, that it cannot handle existence of directories of other users under the same directory as mine.
Otherwise it could be that somebody changed the permissions during the update.

---

### Post by Morbius1 on 2017-05-17
I'm confused by your workaround:
> I found a work around in the mean time. One needs to specify as target  directory subdirectory to which user has access rights, followed by "/".  It previously managed to list the parent directory.

Are you talking about a connection from your Linux file manager / smbclient  or the mount.cifs mount?

The file manger / smbclient will reference smb.conf whereas mount.cifs doesn't even know smb.conf exists.

More of a side note: There is a parameter in smb.conf that controls the maximum negotiated client smb dialect that can be attained. The default level as you mentioned is SMB1 as shown here when my Linux machine access a win10 share. From my Win10 machine:
> PS C:\WINDOWS\system32> Get-SmbSession | Select Dialect,ClientComputerName,ClientUserName

**[COLOR=#0000cd]Dialect[/COLOR]** ClientComputerName ClientUserName
------- ------------------ --------------
**[COLOR=#0000cd]1.0.1[/COLOR]**   192.168.1.143      VWIN10\SMBUSER
But if I edit smb.conf and add the following line to the [global] section:
```
client max protocol = SMB3
```
And restart smbd the connection is as smb3:
> PS C:\WINDOWS\system32> Get-SmbSession | Select Dialect,ClientComputerName,ClientUserName

**[COLOR=#0000cd]Dialect[/COLOR]** ClientComputerName ClientUserName
------- ------------------ --------------
**[COLOR=#0000cd]3.1.1[/COLOR]**   192.168.1.143      VWIN10\smbuser

In the past setting that parameter to anything above the default ( NT1 ) resulted in breaking browsing by the file manager so you would have to explicitly state the server and share but they seem to have fixed that - at least in this exercise it did.

---

### Post by biff-stu on 2017-05-17
I ran into the same problem. My fix was to edit the smb.conf file to add the following two lines to the [global] section:
client min protocol = SMB2
client max protocol = SMB3

I then restarted smbd.

On some of my machines, I have to specify just the server name when I connect. Once authentication is completed, I can then navigate to the desired share.

(Edited to fix my glaring error of using 'version' instead of 'protocol')

---

### Post by Morbius1 on 2017-05-17
> **biff-stu said:**
> I ran into the same problem. My fix was to edit the smb.conf file to add the following two lines to the [global] section:
client min version = SMB2
client max version = SMB3

I then restarted smbd.

On some of my machines, I have to specify just the server name when I connect. Once authentication is completed, I can then navigate to the desired share.

Did you mean "protocol" instead of "version"?

From my post:
> In the past setting that parameter to anything above the default ( NT1 )  resulted in breaking browsing by the file manager so you would have to  explicitly state the server and share but they seem to have fixed that -  at least in this exercise it did.         
I was working on a new network and I'm afraid the old bug ( not sure if it's smbclient or gvfs ) was still there. Setting "client max protocol" to anything above NT1 makes a mess of browsing so you have to explicitly tell it at least the server as biff-stu pointed out.

---

### Post by biff-stu on 2017-05-17
Oops - let me go back and fix that.

---

### Post by bak&#305;r on 2017-05-18
> **biff-stu said:**
>  My fix was to edit the smb.conf file to add the following two lines to the [global] section:
client min protocol = SMB2
client max protocol = SMB3

I then restarted smbd.


Thank you, this indeed worked. I had not thought of changing the maximum protocol variable, but min protocol. Only setting the min protocol does not help.

To clear my imprecise description that caused confusion: previously access through smbclient AND file manager AND mounting had failed. I realised that I could make smbclient work by forcing SMB3 as in my original post. Then I also realised that if I indicate a folder solely consisting of my files, but its parent folder, I could access it. And now I can confirm that the fix that you proposed works for the file manager as well, so the problem is basically solved.

---

