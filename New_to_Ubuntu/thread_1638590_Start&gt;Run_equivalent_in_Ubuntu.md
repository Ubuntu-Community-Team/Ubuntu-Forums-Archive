---
title: "Start&gt;Run equivalent in Ubuntu"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Sphoneix on 2010-12-05
Hi,

I'm a new to Ubuntu, I switched from Windows and I am quickly falling in love with it. I'm started to get the hang of using the terminal. However I had just one question. I'm trying to access an online download file for school research. The address of the file and username/password for it have been provided to me by the school. The only problem is I don't know how to access it on Ubuntu (I was able to do it on Windows). The instructions that were given are for Windows, I was wondering if there is an equivilant to these instructions in Ubuntu that would allow me to get the files. Here are the Windows instructions:

[COLOR=#800000]> Here are instructions to download the software. Installation instructions[/COLOR]
[COLOR=#800000]> (How to Install MSC Software_2010.doc) are located in the download[/COLOR]
[COLOR=#800000]> directory.[/COLOR]
[COLOR=#800000]>[/COLOR]
[COLOR=#800000]> From a Windows computer, go to Start-Run. Type in:[/COLOR]
[COLOR=#800000]> \\crockett.inst.hssoe.uci.edu\MSC[/COLOR]
[COLOR=#800000]> <file:///\\crockett.inst.hssoe.uci.edu\MSC>[/COLOR]
[COLOR=#800000]> If this doesn't work use the IP address: \\123.456.789.123\MSC[/COLOR]

Then enter username/password.

Any help would be much appreciated. Thank you.

---

### Post by uRock on 2010-12-05
Give alt+F2 a try. I am not sure that syntax will work though.

---

### Post by Sphoneix on 2010-12-05
> **uRock said:**
> Give alt+F2 a try. I am not sure that syntax will work though.

Thank you for the reply,

I tried alt+F2 with both commands given in the instructions and got a similar error for both. Here is the error I received with the IP...

Error stating file '/home/owner/\\123.456.789.123\MSC': No such file or directory

I typed in "\\123.456.789.123\MSC"

---

### Post by dexeqex on 2010-12-05
Hi,

From a terminal Alt+F2 -> gnome-terminal you can try logging in remotely by typing:

ssh 123.456.789.123\MSH

If it's a Linux server you should be able to log in and copy files from there.  If that doesn't work you can try to use ftp by typing the below into the address bar of a web browser. 

[ftp://123.456.789.123\MSH]("ftp://128.195.173.110%5CMSH")

Hope this helps.

---

### Post by shashanksingh on 2010-12-05
The only thing is it should be a linux server.
If its a windows server with windows folder sharing, u'll have to use samba.

---

### Post by Sphoneix on 2010-12-05
> **shashanksingh said:**
> The only thing is it should be a linux server.
If its a windows server with windows folder sharing, u'll have to use samba.

Thanks for the advice, I believe the server is a windows server. I have asked the person in charge to send me information on downloading the files with Linux (just in case they put them somewhere else for easy access for linux users). But she hasn't replied so I tried samba. I've installed it and everything but I am not sure how to use it exactly. I looked online and I typed in this code in the terminal (after setting up my user name and password for samba).
.
.
.

owner@owner-VGN-AR570E:~$ sudo mkdir /mnt/winstuff
owner@owner-VGN-AR570E:~$ smbmount \\123.456.789.123\MSC

Usage:  mount.cifs <remotetarget> <dir> -o <options>

Mount the remote target, specified as a UNC name, to a local directory.

Options:
    user=<arg>
    pass=<arg>
    dom=<arg>

Less commonly used options:
    credentials=<filename>,guest,perm,noperm,setuids,nosetuids,rw,ro,
    sep=<char>,iocharset=<codepage>,suid,nosuid,exec,noexec,serverino,
    mapchars,nomapchars,nolock,servernetbiosname=<SRV_RFC1001NAME>
    directio,nounix,cifsacl,sec=<authentication mechanism>,sign

Options not needed for servers supporting CIFS Unix extensions
    (e.g. unneeded for mounts to most Samba versions):
    uid=<uid>,gid=<gid>,dir_mode=<mode>,file_mode=<mode>,sfu

Rarely used options:
    port=<tcpport>,rsize=<size>,wsize=<size>,unc=<unc_name>,ip=<ip_address>,
    dev,nodev,nouser_xattr,netbiosname=<OUR_RFC1001NAME>,hard,soft,intr,
    nointr,ignorecase,noposixpaths,noacl,prefixpath=<path>,nobrl

Options are described in more detail in the manual page
    man 8 mount.cifs

To display the version number of the mount helper:
    mount.cifs -V

I am not sure how to proceed from here : - /

---

### Post by asmoore82 on 2010-12-05
"Places -> Connect to Server"

"Service type -> Windows Share"

And fill in the info.
Sometimes you must specify the "Share" name or it won't work,
it depends on how the server is configured.
Based on your info, it looks like you need "MSC" in "Share" and leave "Folder" blank.

The "guru" way to do this would involve a url of the form
"smb://<username>@<ip-address>/<share>/<folder>" in nautilus, but I'm not sure.

IMO, smbmount is only for administrators who need persistent and/or transparent mounts.

---

### Post by Sphoneix on 2010-12-05
> **asmoore82 said:**
> "Places -> Connect to Server"

"Service type -> Windows Share"

And fill in the info.
Sometimes you must specify the "Share" name or it won't work,
it depends on how the server is configured.
Based on your info, it looks like you need "MSC" in "Share" and leave "Folder" blank.

The "guru" way to do this would involve a url of the form
"smb://<username>@<ip-address>/<share>/<folder>" in nautilus, but I'm not sure.

IMO, smbmount is only for administrators who need persistent and/or transparent mounts.


THANK YOU! I got in :) ... however all the files are for windows machines (should have suspected that) and the instillation instructions are also for windows (the programs are very sensitive and need to be installed in a specific order in a specific directory) so I'm not sure if these files will work. So I'm going to try it later, if it doesn't I'm just going to wait for our schools IT help to send me the information I requested on how to install on Linux. Thanks for the help everyone I let you guys know what happens.

---

### Post by Mark Phelps on 2010-12-06
From what I saw on the MSC website, these are strictly MS Windows apps.  Forget about installing or running them in Ubuntu using Wine or any of its variants -- that's just NOT going to work.

If you have to use these, your only working choices are going to be the following:
1) Dual-boot system with partitions both for MS Windows and Ubuntu
2) Virtualbox installed inside Ubuntu, with a MS Windows OS installed inside that.

Sorry, but Wine is not the miracle cure some make it out to be.

---

### Post by theozzlives on 2010-12-06
> 

[COLOR=#800000]> Here are instructions to download the software. Installation instructions[/COLOR]
[COLOR=#800000]> (How to Install MSC Software_2010.doc) are located in the download[/COLOR]
[COLOR=#800000]> directory.[/COLOR]
[COLOR=#800000]>[/COLOR]
[COLOR=#800000]> From a Windows computer, go to Start-Run. Type in:[/COLOR]
[COLOR=#800000]> \\crockett.inst.hssoe.uci.edu\MSC[/COLOR]
[COLOR=#800000]> <file:///\\crockett.inst.hssoe.uci.edu\MSC>[/COLOR]
[COLOR=#800000]> If this doesn't work use the IP address: \\123.456.789.123\MSC[/COLOR]

Then enter username/password.

Any help would be much appreciated. Thank you.

+1 for ALT+F2 for the run dialig, but the syntax for the commands will have to be modified (ie: backslashes, \, in Windows are front slashes, /, in Linux even even accessing a Windows network)

---

### Post by walt.smith1960 on 2010-12-06
> **Sphoneix said:**
>  
........
Thanks for the help everyone I let you guys know what happens.

If I were to speculate, I'd guess what will happen is  "What is this......Linux.....you speak of?" ;)

---

