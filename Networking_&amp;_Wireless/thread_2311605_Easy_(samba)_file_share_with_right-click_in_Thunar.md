---
title: "Easy (samba) file share with right-click in Thunar (Xubuntu)"
date: 2016-01-28
forum: Networking &amp; Wireless
---

### Post by berteh on 2016-01-28
Hello,

To easily share directories on your local network from Thunar (using Samba in Xubuntu or other XFCE), simply add the following custom actions in Thunar > Edit Menu > Custom Actions.  Shared directories will be visually tagged with the "web" emblem... until you put an end to the share using the third action below.

It works great to access local files from mobile devices on your home network, eg with the free [ES File Explorer App]("https://play.google.com/store/apps/details?id=com.estrongs.android.pop") on Android, or any other Samba-client app.

Safe(ish) read-only share:
[LIST]
[*]Name: Share (RO)
[*]Description: Share Directory with Samba (Read Only)
[*]Command: [FONT=Courier New][SIZE=1]net usershare add %n %f "" Everyone:R guest_ok=y  && chmod 775 %f &&  gvfs-set-attribute %f -t stringv metadata::emblems emblem-web[/SIZE][/FONT]
[*]Appears if selection contains: Directories
[/LIST]

Risk(ier) read-write share:
[LIST]
[*]Name: Share (RW)
[*]Description: Share Directory with Samba (Read Only)
[*]Command: [FONT=Courier New][SIZE=1]net usershare add %n %f "" Everyone:F guest_ok=y  && chmod 777 %f &&  gvfs-set-attribute %f -t stringv metadata::emblems emblem-web[/SIZE][/FONT]
[*]Appears if selection contains: Directories
[/LIST]

To cancel any of the above shares:
[LIST]
[*]Name: UnShare
[*]Description: End sharing of this Directory with Samba
[*]Command: [FONT=Courier New][SIZE=1]net usershare delete %n  &&  gvfs-set-attribute %f -t stringv metadata::emblems none[/SIZE][/FONT]
[*]Appears if selection contains: Directories
[/LIST]

Make sure samba is installed, of course:
```
sudo apt-get install samba
```

To list all active shares run the following command from a terminal:
```
net usershare list
```

And please read the [documentation of Samba]("https://www.samba.org/samba/docs/using_samba/ch09.html") for more accurate settings that may a.o. provide more secure settings:

Thanks to [CryNGRoad]("http://ubuntuforums.org/showthread.php?t=1845244&p=11505823#post11505823") and [Seth]("http://askubuntu.com/a/408954") for providing elements of this cool trick.

Berteh.



PS: If you would rather not configure it all by hand and still get the same result, just run the commands below in a terminal to get all 3 actions added for you.
```
CONTENT='<action> <icon>preferences-system-sharing</icon> <name>Share (R)</name> <command>net usershare add %n %f &quot;&quot; Everyone:R guest_ok=y &amp;&amp; chmod 775 %f &amp;&amp; gvfs-set-attribute %f -t stringv metadata::emblems emblem-web</command> <description>Share Directory with Samba (Read Only)</description> <patterns>*</patterns> <directories/> </action> <action> <icon>preferences-system-sharing</icon> <name>Share (RW)</name> <command>net usershare add %n %f &quot;&quot; Everyone:F guest_ok=y &amp;&amp; chmod 777 %f &amp;&amp; gvfs-set-attribute %f -t stringv metadata::emblems emblem-web</command> <description>Share Directory with Samba (Read &amp; Write)</description> <patterns>*</patterns> <directories/> </action> <action> <icon>preferences-system-sharing-symbolic</icon> <name>UnShare</name> <command>net usershare delete %n &amp;&amp; gvfs-set-attribute %f -t stringv metadata::emblems none</command> <description>End sharing of this Directory with Samba</description> <patterns>*</patterns> <directories/> </action> </actions>'
cat $HOME/.config/Thunar/uca.xml >> newtmp
sed 's/<\/actions>//' <newtmp >newfile
echo $CONTENT >> newfile
mv $HOME/.config/Thunar/uca.xml $HOME/.config/Thunar/uca.xml.bak
mv newfile $HOME/.config/Thunar/uca.xml
rm newtmp

```

---

