---
title: "Viewing Vista network through ubuntu?"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by aperture123 on 2010-10-30
Hello again Ubuntu community!

  I am an avid user of ubuntu, and installed 10.04 on my netbook (getting away from the old XP). However, my main desktop computer uses Vista (I haven't been entirely successful in convincing others to let me 'fix' it). Now the other computers in my house use windows variants (another XP and a 7) and they can all connect to my workgroup network on the vista, able to share and transfer files throughout the house. However, when I click 'network' folder from the places menu, another folder shows up that says 'Windows Network'. Inside of that folder is a folder that has 'WORKGROUP' on it, but Ubuntu just does not connect to it. It always freezes up or gives some sort of error regarding it. 

Is this because I'm connecting to the wireless router with ubuntu, or what? I did some searching and all I found was something called 'samba'...is that what I need to connect to my share of folders on my network? I disabled the WEP by the way, and there's no password protection on my files (risky yes, but I'm at the point of desperation right now).

Any ideas?

---

### Post by starcraft.man on 2010-10-30
Please re-enable encryption on your router unless you've nothing to lose and have your machines secured somehow.

As to sharing files, this is a good guide:
[http://www.n00bsonubuntu.net/content/install-samba-and-share-folders-ubuntu-1010-maverick-meerkat](http://www.n00bsonubuntu.net/content/install-samba-and-share-folders-ubuntu-1010-maverick-meerkat)

Condensed version is:

command (on any terminal):
sudo apt-get install samba pyneighborhood system-config-samba.

System-config-samba is a GUI tool that is shown in the tut, lets you set up the shares on the Ubuntu machine to share to others.

pyneighborhood is a tool to browse the shares on a network, works well for me. Click around it's pretty intuitive.

Programs available under System > Administration > Samba and Applications > System Tools respectively. 

I've never found the built in sharing/browsing that reliable. /grumpy voice

Doubt there's any trouble after that.

---

### Post by Morbius1 on 2010-10-30
> As to sharing files, this is a good guide:
[http://www.n00bsonubuntu.net/content...verick-meerkat]("http://www.n00bsonubuntu.net/content/install-samba-and-share-folders-ubuntu-1010-maverick-meerkat")That's another in a growing family of samba howto's that combine two entirely different methods of creating samba shares into one procedure.

First he creates a share using system-config-samba which will create a share definition in /etc/samba/smb.conf.

Then he creates the share all over again using nautilus-share ( Nautilus > Sharing Options ) which will create a share definition at /var/lib/samba/usershares

The whole thing is very curious. My recommendation if you're just starting out is to use Nautilus-share ( Nautilus > Right Click a folder you own > Sharing Option > click on all the options ).

But to get back to your original question - if you're trying to access a Vista share you don't need samba at all. Run the following command and post the output:
```
smbtree
```Perhaps pyneighborhood is the way to go. Never used it. For some reason samba has never been a issue in my home network.

---

### Post by starcraft.man on 2010-10-30
> **Morbius1 said:**
> That's another in a growing family of samba howto's that combine two entirely different methods of creating samba shares into one procedure.

First he creates a share using system-config-samba which will create a share definition in /etc/samba/smb.conf.

Then he creates the share all over again using nautilus-share ( Nautilus > Sharing Options ) which will create a share definition at /var/lib/samba/usershares

The whole thing is very curious. My recommendation if you're just starting out is to use Nautilus-share ( Nautilus > Right Click a folder you own > Sharing Option > click on all the options ).

But to get back to your original question - if you're trying to access a Vista share you don't need samba at all. Run the following command and post the output:
```
smbtree
```Perhaps pyneighborhood is the way to go. Never used it. For some reason samba has never been a issue in my home network.

Oddly enough, using the built in nautilus share has been crashing my nautilus every single time on my new clean install of meerkat. I forgot that guide mixed in the nautilus way too, not sure why author did so. The gui tool + py work nice and consistently. 

Maybe I'm just unlucky what with my sharing environs. :/

---

### Post by Morbius1 on 2010-10-30
> I forgot that guide mixed in the nautilus way too, not sure why author did so.I have a theory. If you use system-config-samba and create a writable guest share at say ... /home/user/Documents it won't work because the permissions on that directory are 755. The guest is "other" and he only has read access.

If you then use nautilus-share on the same target folder it will automatically modify the Documents folder permissions to 777. Problem solved. Of course now you have two share definitions in play and eventually this will cause a problem but ...

He could have used a chmod or used Nautilus itself to change permissions but maybe the author didn't know that.

Just a theory :)

---

### Post by aperture123 on 2010-10-31
Alright, I followed that guide on Samba after the sudo apt-get install with py gui and all that.... did everything in the guide but got stuck here...

> "sudo chmod o+w YOURSHAREDFOLDER/filename"^This did not work. However, I am happy to admit that under Network THOMAS-LAPTOP did indeed show up, although it required a username and password. Strangely, this turned out to be an email address, but I was able to get in...and see Shared-10.10!!! :D
Next up...smbtree gave me this..

```
thomas@thomas-laptop:~$ smbtree
Enter thomas's password: 
WORKGROUP
    \\THOMAS-PC              
cli_start_connection: failed to connect to THOMAS-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\THOMAS-LAPTOP          
        \\THOMAS-LAPTOP\IPC$               IPC Service (thomas-laptop server (Samba, Ubuntu))
        \\THOMAS-LAPTOP\print$             Printer Drivers
        \\THOMAS-LAPTOP\Shared-10.10       
    \\BRI-PC                 
cli_start_connection: failed to connect to BRI-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

```
Bri-PC is my other pc we have in the house, but thoams-pc is my actual vista computer...


So now my vista can access my ubuntu, but I still need ubuntu to be able to access THOMAS-PC. Any ideas how?

---

### Post by Morbius1 on 2010-10-31
The usual suspect in this sort of thing is a firewall is in the way. Since Vista can access Ubuntu it's not likely a firewall on Ubuntu. Disable the Vista firewall and see if you can connect.

It could be a name resolution problem - converting "THOMAS-PC" to an actual ip address. See if you can access the Vista machine directly by ip address:

in a terminal:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the actual ip address of the Vista machine.*[/COLOR]

You could at that point "Bookmark" the location in Nautilus: Bookmarks > Add bookmark. THen it will show up under Places in Nautilus just like a "mapped drive" does in Windows.

---

### Post by aperture123 on 2010-11-06
Thanks to all posters, I got it working!

It took some work, but samba did everything I needed, and I was able to contact and 'bookmark' my vista machine, which was awesome concerning file management and managing a HUGE itunes library. Sadly, my vista just blew out (power supply issue), but now I don't mind. All my data just so happens to be backed up to a much...safer computer. Linux. ;)

Thanks again everyone.

---

