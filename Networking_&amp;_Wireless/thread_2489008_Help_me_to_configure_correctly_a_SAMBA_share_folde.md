---
title: "Help me to configure correctly a SAMBA share folder :("
date: 2023-07-15
forum: Networking &amp; Wireless
---

### Post by DjDiabolik on 2023-07-15
Hi boys... recently i have installed Ubuntu 22.04.2 on my Intel NUC NUC7PJYHN.

All apparently working...... it's a my idea to add a "Shared" Folder for use that from my other pc in my home. All apparently it's very easily but i can't do make it work correctly.

Need to do a little recap: the first thing i did it's create a new folder on "Home" path. Folder name "Condivisi" (it's in /home/diabolik/Condivisi).
From Desktop and from built in "file manager" selected that Folder and enable the "Shared option" inside folder "Properties"

If i understand correctly that things use the command 'net usershare add' to activate the samba sharing. Infact it's will ask to me to install samba. I accept all request and apparently sharing should work. But NO.. It's no WORK.

- I went to my other PC. This PC it's a Windows PC! Windows 10 X64 22H2 build 19045.3208 whit all last patch installed from Windows Update.
- Open windows "Esplora Risorse" (whit WIN+E) put ""\\192.168.1.6\" on address bar
- Windows ask me a login. I've tried everything here and nothing works! I have tryed to use my same credentials used to login Ubuntu (user -> diabolik and my password) NO WORK. I have tryed to use my "Microsoft Account" credential used to login at boot windows 10 (user -> djdiabolik<at>mymail.it <- mymail.it it's not my real email..) ... NO WORK. 

After a lot of research by google and read (and made a lot of addictional confusion on my head) i have poorly understand i need to create a samba user password for my ubuntu username. This is not written anywhere... but i did this:
- add my username to 'sambashare' group whit:
```
sudo usermod -g sambashare diabolik
```
Source of this here -> [https://linuxwizardry.com/how-to-manage-users-and-groups-on-ubuntu-22-04/](https://linuxwizardry.com/how-to-manage-users-and-groups-on-ubuntu-22-04/) <- I hope all it's correct here... lol.

- after that create a samba password for my account whit:
```
 sudo smbpasswd -a diabolik
```

in theory after doing this I go back to my Windows PC... tryed again on "Esplora Risorse" and DAMMNN... it's not works AGAIN.. Windows made my crazy and can't connect.

After that first test I probably made another ten attempts to try to understand how SAMBA need to configure correctly on ubuntu. All whitout insuccess..... look right now an example... the output of:
```
getent group
```

It's like this:
```
diabolik:x:1000:
sambashare:x:136:diabolik,osmc,djdiabolik@mymail.it
djdiabolik@mymail.it:x:999:
osmc:x:998:
testshare:x:997:shareusers
shareusers:x:996:
```

Look what a confusion..... i have tryed to add some other user to "sambashare" group and NO HELP. I have tryed to create all other user djdiabolik@, osmc and NO HELP.
Recently i have also try to create the group 'testshare' and add user shareusers to that. BUT NO WORK.

For create all tested user i have googled and used that command:
```
sudo useradd --system --no-create-home --group testshare -s /bin/false shareusers
```
In this example i have created 'shareusers' and i have add directly to group 'testshare'. I thinks it's correct... for other user sometime i use a more general command like:
```
sudo useradd --system --no-create-home -s /bin/false osmc
```

Obviously all this user, after create that, i have created his 'smbpasswd -a'  but NO HELP... NO WORKS AT ALL. Samba shares it's not works.



For try to understand how i tested currently i have also to add my 'ex-novo' smb.conf files... now it's like that:
```
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = NUC-Ubuntu
security = user
map to guest = bad user
dns proxy = no

[sharetest]
comment = All Users
path = /home/diabolik/sharetest
valid users = @testshare
force group = testshare
create mask = 0660
directory mask = 0771
writable = yes
```

but no way.... Samba can't ever accessible from Windows ever if i use the GUI Method (from desktop and for folder /home/diabolik/Condivisi) or ether if i use smb.conf method (for '/home/diabolik/sharetest' folder)

It's need some help here....... lol:

You can see here i have messed aroud whit my current Samba configuration (and also possibly whit ubuntu user).
how can i do some cleaning? For example how i can reset my current smb.conf to reobtain the default ubuntu smb.conf whitout need to do a "complete formatting" and a new installation of ubuntu ? It's exist one method ?

Other things.... i can delete some group/user not needed at right now ? If yes how i can do whitout make my ubuntu completely in crash ? 

Thanks in advance for every suggestion you can write to me.......

---

