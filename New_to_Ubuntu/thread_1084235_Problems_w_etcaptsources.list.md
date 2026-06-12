---
title: "Problems w/ /etc/apt/sources.list"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by EnioG on 2009-03-01
PLSSSS can anyone help me???? I'm a switcher from windows and just installed ubunto 8.10 after 4 hours of problems(pc would just freeze).

Now that its up and running I can't use synaptic product manager or update manager! It keeps saying error but doesn't tell me what the error is....Also the sources list or packages (whatever u call it) is non existent!!! 

I tried to use apt- but is says 
E: Type ‘&#65533;&#65533;uh'&#65533;&#65533;g&#65533;Z&#65533;nB&#65533;&#65533;&#65533;&#899079;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;f&#65533;&#1868;&#65533;&#65533;&#65533;w=~&#65533;C&#65533;&#65533;&#65533;w=&#65533;&#1728;:7&#65533;&#65533;’ is not known on line 1 in source list /etc/apt/sources.list
I have also tried to see whats inside it it just comes up with &#65533;&#65533;uh'&#65533;&#65533;g&#65533;Z&#65533;nB&#65533;&#65533;&#65533;&#899079;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;f&#65533;&#1868;&#65533;&#65533;&#65533;w=~&#65533;C&#65533;&#65533;&#65533;w=&#65533;&#1728;:7&#65533;&#65533; sort of thing.

I really dont know what else to do, pls HELP ME!

I'm using a toshiba equium A60
2.8 ghz
I used wubi to install ubuntu.

---

### Post by RomeReactor on 2009-03-01
Hi. That means an entry in your sources is incorrect; open a terminal and run:
```
cat /etc/apt/sources.list
```
and post the output.

---

### Post by EnioG on 2009-03-01
this is what it came up with... pls help


&#65533;&#1600;:6{#|e#t&#65533;D&#65533;&&#65533;&#65533;&#56110;&#56327;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;6&#65533;&#65533;6{&#65533;Z&#65533;vU&#65533;&#65533;j!C-&#65533;oA&#65533;[p~&#1728;:7&#65533;&#65533;
                                                  &#65533;o&#65533;&#65533;f&#65533;&#65533;
                                                         _&#65533;
                                                           &#65533;&#65533;-&#65533;y
                                                                  &#951;&#65533;|+&#951;B&#1965;&#65533;&#65533;V&#65533;&#65533;V&#65533;+&#65533;&#65533;z&#65533;}oC&#65533;&#1760;&#65533;m&#65533;k;l&#65533;6&#1614;&#65533;&#65533;&#65533;&#65533;6|&#65533;6&#65533;&#1998;&#65533;&#65533;q~;&#65533;o&#65533;&#65533;8&#65533;&#65533;w&#65533;&#65533;;&#65533;u'&#65533;r'&#65533;q'&#65533;&#65533;v&#1665;&#65533;vk&#65533;&#65533;|&#65533;&#65533;;&#65533;&#65533;N`&#65533;&#65533;&#65533;.&#65533;&#65533;&#65533;&#65533;.&#65533;S&#65533;&#65533;&#65533;u&#8805;ˆ@_ø&#9618;çÔ]^&#65533;&#65533;k=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533;L&#65533;4@&#973;&#65533;g#&#65533;l?&#65533;(&#1220;&#65533;M&#65533;c&#65533;7&#65533;&#65533;&#65533;(&#65533;
                                                                          &#65533;7&#65533;&#65533;&#65533;xm8oG¿&#9484;‡¿&#9508;Àï;&#9147;Þü&#9252;¡ü&#9508;Â:‘¿&#40721;&#65533;
                               å»P¾
                                   úí‚º¡ï&#9532;&#9670;&#9500;ã¼<ìþö ÿäßƒóðØž&#8805;à_=¡¾¹&#960;Áã^Ø&#9149;/0ö!Ï>È±z&#1799;:&#65533;&#65533;&#65533;.&#65533;&#65533;.&#65533;&#65533;
&#65533;&#61854;&#65533;&#65533;.&#65533;&#65533;=&#65533;&#65533;=hg&#65533;@&#65533;&#65533;&#65533;&#829;&#65533;&#65533;^&#65533;&#65533;~&#65533;1\&#65533;&#65533;&#65533;&#65533;&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Co&#65533;ß&#65533;@&#960;£ Ø&#65533;&#65533;&#65533;&#707;&#65533;&#65533; &#65533;Q=&#65533;zB=&#65533;&#65533;&#26578;&#65533;&#65533;F&#1927;&#65533;&#65533;a\&#65533;&#65533;~&#30656;&#65533;&#65533;&#65533;?]=&#65533;&#65533;&#65533;&#65533;$&#65533;&#65533;$&#65533;&#65533;I&#65533;&#65533;I&#65533;&#65533;S&#65533;&#1255;&#65533;&#65533;S&#65533;&#65533;&#65533; &#995;&#65533;&#65533;&#65533;&#65533;&#1251;(
<&#65533;?&#65533;y
        e&#65533;?=G;y&#65533;e&#65533;O &#65533;<&#65533;2O&#65533;&#65533;'&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;_&#65533;Q&#65533;~&#65533;{&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;a&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;v&#65533;&#65533;G&#65533;&#65533;&#65533;s?&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;<	}?	y&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;,O&#65533;O&#65533;&#65533;'&#65533;&#65533;I&#263;'&#65533;&#65533;&#65533;p&#65533;)&#65533;&#65533;d{
&#65533;g &#65533;3&#65533;&#65533;&#65533;=&#65533;&#65533;g&#65533;&#65533;3&#65533;&#65533;3H&#65533;&#65533;{i&#65533;&#65533;&#65533;>
                     &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;,&#65533;zX&#65533;&#65533;Y&#65533;&#65533;,x&#65533;,&#65533;&#65533;,b&#65533;g!&#65533;g&#65533;&#65533;&#311;&#65533;&#65533;&#65533;;>&#65533;s&#65533;&#65533;&#65533;P&#65533;&#65533;P&#65533;&#65533;P&#65533;s&#65533;&#65533;s&#65533;&#65533;9&#65533;>ñ<ä£&#9228;ç!ãóHú&#8804;é/Àþ/*ì
                              íèóÈöúŸPï‹àûE\&#9226;^D™&#9472;ýE\&#960;&#8800;¼„º^BúKH	é/Aÿ/ÁÆ/£/é/ƒç—&#9618;‡—¡§—!ë+¨çØòÈö
Ò_A¯B–W!Ë«°Ù«°É&#9488;ÿ5ÈòÊ¾†<¯!Ïç&#9618;£Ï#V·Ÿ‡._‡¯CG¯£Üë&#9252;+¯ƒŸ/€Ï/À¾ ù¿ ù¿ »£å¾ˆ&#8800;_„&#9492;]-8ýÙõ8·‹¬*O?"'•‘J¿:&#9146;ª6H&#9146;úÚAƒøÁž¬^—êÀ&#9227;YÄ¥#°È$&#9148;‰šàÉî÷AßA„"¥;#P4(*V&#9500;¯Ê·C•&#9228;š
+&#9492;B&#9146;±·Pÿ×AEú°&#9252;8–ÉC*2´¦‰<&#9149;é“&#9508;ž&#9226;•!£*øÝ€òßÄù;L8þ-ÊÜÖ«
                                                           $
                                                             I€&#9524;œ
&#65533;ò!¥“&#9226;$&#65533;q&#65533;&#65533;7!&#65533;g&#65533;&#65533;F}&#65533;i&#65533;&#65533;&#65533;T&#65533;&#65533;d)JO&#65533;W%
                  &t|&#65533;b_&#65533;P&#65533;&#65533;&#65533;&#65533;E&#65533;&#65533;j&#65533;&#65533;mv&#65533;#E;<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;¦ƒJ7Z9ŠØ7OÍQ¤&#9508;&#9492;–Ý¥°´^ûF–‡Ï¤®ó#C&#9228;(ÖÏXÎ·=&#8805;&#960;ä·\_Â&#9532;HÂ°Ú>_ýBñ©&#9508;°‘&#9229;[0&#9492;4Í¸æ&#9618;ŠGŸ£†ìñ6£MË&#9146;Ó×*ÉõW+âê©V¥Õªó4&#9508;ýˆ"Þô&#9472;¼&#8800;Þ&#8805;Ø¯Ð!:=ÇöÚ‡´U*"&#9148;&#9508;™A&#9149;&#9147;0™ª*ð•è1Ö"Ê¿ÈA&T&#9500;½ã×›ÖÖºíL•,+?L£@Ùà+T†B*&#9472;**ä«
          ËNÿ&#9618;&#9227;ï•È³Â*•H«ã&#9228;ä&#65533;&#65533;8n&#65533;&#65533;'&#65533;&#65533;'&#65533;&#65533;}&#65533;e\&#65533;%'Z_8©&#9488;+ÎÅO8âÚ±&#9618;&#9508;êW§…U>&#9492;_&#9226;õ&.&#65533;&#65533;%i&#65533;U&#65533;&#65533;&#65533;&#471;&#65533;&#65533;/~:&#65533;&#62403;?&#65533;v>X\7&#65533;&#65533;*&#65533;~&#65533;kGns
&#65533;/&#65533;Hd9&#65533;&#65533;4}&#65533;&#65533;&#65533;&#65533;&#65533;       &#65533;"&#65533;O!L_&#65533;&#65533;q-&#65533;6&#1077;&#65533;rEd!&#65533;b&#65533;&#65533;G&#65533;f&#65533;&#65533;j&&#65533;UJ}W&#65533;&#65533;&#65533;&#65533;&#65533;H&#65533;ZUo&#65533;&#65533;y‚Ã&#9472;ÊY½²’Á&#9147;7*&#960;ð¹ã£¬&#960;È&#8804;ÉØÏ1”«é#&#9516;
                         Ãñ=M&#9618;ðó×3_!©ÿƒ*Î&#9496;7FFcIb9&#65533;jQ&#65533;&#65533;&#65533;o&#65533;#&#65533;&#65533;&#65533;
v&#65533;
*&#65533;&#65533;&#65533;&#65533;3&#65533;Z&#65425;r&#65533;/&#65533;&#65533;<2&#65533;&#65533;&#65533;^&#65533;}#BUo&#65533;&#827;&#65533;K*&#65533;&#65533;'&#65533;&&#65533;U&#65533;&#65533;Mj&#65533;&#65533;~&#65533;EmX&#65533;
                                                       &#65533;e&#65533;&#1783;&#65533;&#65533;&#65533;&#65533;&#65533;<&#65533;Od&#65533;&#65533;)&#65533;&#65533;&#65533;e&#65533;&#65533;&#65533;VF&#65533;M&#65533;_&#65533;&#65533;&#65533;>?&#65533;&#65533;&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;7&#65533;&#65533;&#65533;&#65533;&#65533;J=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;F&#65533;9&#65533;&#65533;&#37628;&#65533;&#65533;tE~&#65533;.&#65533;&#65533;_&#65533;&#498;`&#65533;&#65533;Lx&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;*/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;q9&#1448;&#65533;}&#65533;&#65533;&#1020;&#65533;2&#9472;·L.¢ãƒ&#9474;ºÑã*&#9492;§
                                   Õµ·ã§O§Ø&#9472;ÇG	ê&#9226;9&“Ûç¦ø&#9492;_S¿Â°™ß"·ï°ÝT“ŒÜ&#9147;;„&#9488;ÓOUšW/Œ¿	´%&#9532;Þ
                      «&#9474;ëˆÇ›¶¯Þô8×Oô‘&#9488;&#9146;‡ûÓ&#9225;&#9474;A7*YÙöº@S’·&#9474;¼®èïQÙô+KÒ¯K=ý=&#9227;;¿‡´™×&#65533;&#65533;c&#65533;&#65533;&#899;&#65533;_ÖË&#9146;”ÎÉÍ:„ÈN[êS&#8804;§&#9227;ÈŸ?&#9532;Uå·™@.&&#9532;&#960;&#8800;Ç…õÄç&#9484;Gž“òø&#8800;Çÿ&#9508;<ùåT&#9227;“

---

### Post by RomeReactor on 2009-03-01
Your sources.list is corrupted. Did you modify it prior to this problem?

---

### Post by EnioG on 2009-03-01
not at all. This is a fresh installation, untouched. 
Do you have any idea how to correct the sources.list??

Thanks for replying so quick!!!

---

### Post by louieb on 2009-03-01
try this press **alt+F2** and enter ```
gksudo gedit /etc/apt/sources.list 
```replace whats there with 

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse


```then open a terminal window (applications>accessories>terminal)and run
```
sudo aptitude update
```that should set you up.

---

### Post by RomeReactor on 2009-03-01
Are you located in the US? If so, open a terminal and run this:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
```
then:
```
gedit ~/sources.list
```
paste the following there:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```
Save the file, close Gedit, and:
```
sudo cp ~/sources.list /etc/apt
```
and reload the repository information:
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by EnioG on 2009-03-01
Hi, I tried rome reactor's way and this is what happened
homepc@ubuntu:~$ sudo cp ~/sources.list /etc/apt
cp: cannot stat `/home/homepc/sources.list': No such file or directory
homepc@ubuntu:~$ sudo aptitude update && sudo aptitude safe-upgrade
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

And I also tried louieb's way and after when i tried to use update manager or synaptics product manager this is the error:
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by EnioG on 2009-03-01
Thanks for any help you might give me now but i'll have to try tomorrow..have to work now... Thanks a million!!! oh and I dont live in the us but uk.

---

### Post by RomeReactor on 2009-03-01
> **EnioG said:**
> Hi, I tried rome reactor's way and this is what happened
homepc@ubuntu:~$ sudo cp ~/sources.list /etc/apt
cp: cannot stat `/home/homepc/sources.list': No such file or directory
Make sure you save the file before running the rest of the commands; you should be able to see the sources.list file you just created in your home directory.

> homepc@ubuntu:~$ sudo aptitude update && sudo aptitude safe-upgrade
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

And I also tried louieb's way and after when i tried to use update manager or synaptics product manager this is the error:
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
These errors mean the package manager can't find the sources.list file; that's understandable if you already ran the first command in my previous post, which essentially renamed the file to sources.list.backup.

---

### Post by bodhi.zazen on 2009-03-01
Your terminal is corrupted. This usually happens when you open a binary file or some such.

Close and re-open the terminal and the text should go back to normal.

---

### Post by EnioG on 2009-03-02
now I'm getting 

E:Unable to parse package file /var/lib/dpkg/status (1), E:The package lists or status file could not be parsed or opened.

And I still cant open update manager or synaptics. Any Ideas? Thanks!!!!!!!!!

---

### Post by RomeReactor on 2009-03-02
Did you make sure you followed the steps in the previous page correctly? If so, there should be a sources.list file in /etc/apt. Run:
```
cat /etc/apt/sources.list
```
and post back the contents.

---

### Post by EnioG on 2009-03-02
Hi, this is what happened:
homepc@ubuntu:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse

---

### Post by RomeReactor on 2009-03-02
Your sources.list file looks fine now, so the problem is most likely /var/lib/dpkg/status. Run:
```
ls /var/lib/dpkg
```
if you see a file named **status-old**, then make a backup of the current status file (make sure no package manager is open at this time--Synaptic, Update Manager, Add/Remove, etc):
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
```
and copy status-old as status:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
Lastly:
```
sudo aptitude update && sudo aptitude safe-upgrade
```
And post back how it goes.

---

### Post by EnioG on 2009-03-02
I did exactley what u said but it came up with the same error:

homepc@ubuntu:~$ ls /var/lib/dpkg
alternatives   cmethopt        info   statoverride      status-BROKED  updates
available      diversions      lock   statoverride-old  status-old
available-old  diversions-old  parts  status            triggers
homepc@ubuntu:~$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
homepc@ubuntu:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
homepc@ubuntu:~$ sudo aptitude update && sudo aptitude safe-upgrade
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security Release.gpg       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Translation-en_GB
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Sources
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

---

### Post by RomeReactor on 2009-03-02
There are backups of the status file in /var/backups; try following the instructions posted [here]("http://ubuntuforums.org/showpost.php?p=5046486&postcount=4").

---

### Post by EnioG on 2009-03-02
still comes up with
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

what do you think is the problem with this package???

---

### Post by EnioG on 2009-03-02
I tried 
"sudo apt-get update" and came up with this:
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

So i tried "sudo dpkg --configure -a" which i found while googling and it came up with this:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 47 package `language-pack-gnome-es':
 duplicate value for user-defined field `'

Do have any idea what this is??

---

### Post by RomeReactor on 2009-03-02
Not sure what else to suggest; the few times I've seen this problem come up it was fixed by the instructions you've followed so far. I'm out of ideas at the moment. In any case, you should make backups of important files/data you have on the system; in case no-one else gives you a more adequate answer, you might try reinstalling.

However, be patient and give people a chance to provide you with a solution for this problem.

EDIT: > So i tried "sudo dpkg --configure -a" which i found while googling and it came up with this:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 47 package `language-pack-gnome-es':
duplicate value for user-defined field `'

Do have any idea what this is??
Was there anything else beyond **duplicate value for user-defined field `'**? That would help defining the problem. Editing the file and correcting the problem there doesn't usually work, though.

---

### Post by EnioG on 2009-03-02
dpkg: parse error, in file `/var/lib/dpkg/status' near line 47 package `language-pack-gnome-es':

That's all it came up with....
I hope i dont have t reinstall....

---

### Post by bodhi.zazen on 2009-03-02
This behavior is unusual with a fresh install. I suggest you check the integrity of your ubuntu iso and the quality of the burn (check the cd for errors). You can boot the CD and at the first menu check media ;)

---

