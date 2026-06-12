---
title: "Duplication in &quot;Open With&quot; dialog"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by llakais on 2010-06-08
Hello,

This is rather low-priority as everything seems to be working fine, but I was wondering if anyone could explain this anomaly to me.

I'm using Ubuntu 10.04 LTS, via the Wubi installer for Windows.

I needed to open lots of .xps documents, and so I thought I would see if I could do it in Ubuntu instead of booting Windows.  Document Viewer did not do the trick, but I did find an application called Okular using the Software Center.  However, the Software Center would not let me download it, as it contained "restricted packages."  (Something to do with it using KDE, I think.)

To get around this, I opened the Synaptic Package Manager and found the application there.  It asked me to mark many associated packages, which I did.  I then downloaded and installed them all.

I now can view .xps files using Okular, which is awesome.  It's always nice to be able to accomplish things without Windows.

However, the only oddity is that when I bring up the "Open With" dialog (which I had to do at first to specify Okular for .xps files), Okular is listed a total of 12 times in that menu!

Again, this is certainly not a pressing issue, but I am curious.  "Brasero," "F-Spot," and "Remote Desktop Viewer" all show up twice in the "Open With" dialog as well, but it was the twelve Okular entries that led me to notice any sort of duplication in the first place.

All of the duplicated entries have the "remove" button grayed out, so I can't get rid of them that way.

Anyway, thanks for reading and I hope I haven't bored you to death.

---

### Post by bcbc on 2010-06-10
I just tried this and I see duplicate entries too. In some cases (Brasero) there is a slightly different description (below the list box), in others there is no description.

[This thread]("http://ubuntuforums.org/showthread.php?t=408274") is from someone who wants to delete an entry. But it shows where the "Open with other application" list comes from, and if you look at each entry you can see the differences (if any). Perhaps also delete them.

e.g. ```
$ cat /usr/share/applications/brasero.desktop
[Desktop Entry]
Name=Brasero
GenericName=Disc Burner
Comment=Create and copy CDs and DVDs
Categories=GNOME;AudioVideo;DiscBurning;
MimeType=application/x-cd-image;application/x-cdrdao-toc;application/x-cue;application/x-toc;audio/x-scpls;audio/x-ms-asx;audio/x-mp3-playlist;audio/x-mpegurl;application/x-brasero;
Exec=brasero %U
Icon=brasero
StartupNotify=true
Terminal=false
Type=Application
X-GNOME-FullName=Brasero Disc Burner
X-GNOME-FullName[ar]=&#1581;&#1575;&#1585;&#1602; &#1575;&#1604;&#1571;&#1602;&#1585;&#1575;&#1589; &#1576;&#1585;&#1575;&#1587;&#1610;&#1585;&#1608;
X-GNOME-FullName[as]=Brasero &#2465;&#2495;&#2488;&#2509;&#2453; &#2476;&#2494;&#2544;&#2509;&#2472; &#2476;&#2509;&#2479;&#2545;&#2488;&#2509;&#2469;&#2494;
X-GNOME-FullName[ast]=Grabador de discos Braseru
X-GNOME-FullName[be]=&#1044;&#1072;&#1089;&#1090;&#1072;&#1089;&#1072;&#1074;&#1072;&#1085;&#1100;&#1085;&#1077; &#1076;&#1083;&#1103; &#1079;&#1072;&#1087;&#1110;&#1089;&#1091; &#1076;&#1099;&#1089;&#1082;&#1072;&#1118; Brasero
X-GNOME-FullName[bg]=&#1047;&#1072;&#1087;&#1080;&#1089; &#1085;&#1072; &#1076;&#1080;&#1089;&#1082; (Brasero)
X-GNOME-FullName[bn]=&#2476;&#2509;&#2480;&#2494;&#2488;&#2494;&#2480; &#2465;&#2495;&#2488;&#2509;&#2453; &#2476;&#2494;&#2480;&#2509;&#2472;&#2494;&#2480;
X-GNOME-FullName[bn_IN]=Brasero &#2465;&#2495;&#2488;&#2509;&#2453; &#2476;&#2494;&#2480;&#2509;&#2472; &#2476;&#2509;&#2479;&#2476;&#2488;&#2509;&#2469;&#2494;
X-GNOME-FullName[br]=Engraverez kantennoù Brasero
X-GNOME-FullName[ca]=Enregistrador de discs Brasero
X-GNOME-FullName[ca@valencia]=Enregistrador de discs Brasero
X-GNOME-FullName[cs]=Vypalovací software Brasero
X-GNOME-FullName[da]=Brasero diskbrænder
X-GNOME-FullName[de]=Brasero CD/DVD-Brennprogramm
X-GNOME-FullName[el]=&#917;&#966;&#945;&#961;&#956;&#959;&#947;&#942; &#949;&#947;&#947;&#961;&#945;&#966;&#942;&#962; &#948;&#943;&#963;&#954;&#969;&#957; Brasero
X-GNOME-FullName[en_GB]=Brasero Disc Burner
X-GNOME-FullName[es]=Grabador de discos Brasero
X-GNOME-FullName[et]=Brasero plaadikirjutaja
X-GNOME-FullName[eu]=Brasero, diskoak grabatzea
X-GNOME-FullName[fi]=Brasero-levynkirjoittaja
X-GNOME-FullName[fr]=Gravure de disque Brasero
X-GNOME-FullName[ga]=Dóire Dioscaí Brasero
X-GNOME-FullName[gl]=Gravador de discos Brasero
X-GNOME-FullName[gu]=Brasero &#2721;&#2751;&#2744;&#2765;&#2709; &#2732;&#2728;&#2750;&#2741;&#2728;&#2750;&#2736;
X-GNOME-FullName[he]=&#1510;&#1493;&#1512;&#1489; &#1492;&#1491;&#1497;&#1505;&#1511;&#1497;&#1501; &#1513;&#1500; Brasero
X-GNOME-FullName[hi]=&#2348;&#2381;&#2352;&#2375;&#2360;&#2375;&#2352;&#2379; &#2337;&#2367;&#2360;&#2381;&#2325; &#2348;&#2352;&#2381;&#2344;&#2352;
X-GNOME-FullName[hu]=Brasero lemezíró
X-GNOME-FullName[it]=Masterizzatore dischi Brasero
X-GNOME-FullName[ja]=Brasero &#12487;&#12451;&#12473;&#12463;&#20316;&#25104;&#12484;&#12540;&#12523;
X-GNOME-FullName[kn]=Brasero &#3233;&#3263;&#3256;&#3277;&#3221;&#3277; &#3244;&#3248;&#3257;&#3223;&#3262;&#3248;
X-GNOME-FullName[ko]=&#48652;&#46972;&#49464;&#47196; &#46356;&#49828;&#53356; &#44413;&#44592; &#54532;&#47196;&#44536;&#47016;
X-GNOME-FullName[ku]=Brasero Nivîskarê Dîskan
X-GNOME-FullName[lt]=CD/DVD rašymas bei kopijavimas
X-GNOME-FullName[ml]=&#3372;&#3405;&#3376;&#3384;&#3399;&#3377;&#3403; &#3361;&#3391;&#3384;&#3405;&#3349;&#3405; &#3372;&#3376;&#3405;*&#3363;&#3376;&#3405;*
X-GNOME-FullName[mr]=Brasero &#2337;&#2367;&#2360;&#2381;&#2325; &#2348;&#2352;&#2381;&#2344;&#2352;
X-GNOME-FullName[nb]=Brasero brenneprogram
X-GNOME-FullName[nl]=Brasero cd's branden
X-GNOME-FullName[or]=Brasero &#2849;&#2879;&#2872;&#2893;&#2837; &#2866;&#2887;&#2838;&#2837;
X-GNOME-FullName[pa]=&#2604;&#2608;&#2622;&#2616;&#2624;&#2608;&#2635; &#2593;&#2623;&#2616;&#2581; &#2604;&#2608;&#2600;&#2608;
X-GNOME-FullName[pl]=Nagrywanie p&#322;yt Brasero
X-GNOME-FullName[pt]=Aplicação de Gravação de Discos Brasero
X-GNOME-FullName[pt_BR]=Gravador de Discos Brasero
X-GNOME-FullName[ro]=Scriere de discuri Brasero
X-GNOME-FullName[ru]=&#1055;&#1088;&#1080;&#1083;&#1086;&#1078;&#1077;&#1085;&#1080;&#1077; &#1076;&#1083;&#1103; &#1079;&#1072;&#1087;&#1080;&#1089;&#1080; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074; Brasero
X-GNOME-FullName[sl]=Brasero zapisovalec
X-GNOME-FullName[sr]=&#1041;&#1088;&#1072;&#1079;&#1077;&#1088;&#1086; &#1087;&#1080;&#1089;&#1072;&#1095; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1072;
X-GNOME-FullName[sr@latin]=Brazero pisa&#269; diskova
X-GNOME-FullName[sv]=Skivbrännaren Brasero
X-GNOME-FullName[ta]=&#2986;&#3021;&#2992;&#3006;&#3000;&#2992;&#3019; &#2997;&#2975;&#3021;&#2975;&#3009; &#2958;&#2996;&#3009;&#2980;&#3007;
X-GNOME-FullName[te]=&#3116;&#3149;&#3120;&#3128;&#3142;&#3120;&#3147; &#3105;&#3135;&#3128;&#3149;&#3093;&#3137; &#3116;&#3120;&#3149;&#3112;&#3120;&#3149;
X-GNOME-FullName[th]=&#3650;&#3611;&#3619;&#3649;&#3585;&#3619;&#3617;&#3648;&#3586;&#3637;&#3618;&#3609;&#3649;&#3612;&#3656;&#3609; Brasero
X-GNOME-FullName[tr]=Brasero Disk Yazma Program&#305;
X-GNOME-FullName[uk]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072; &#1076;&#1083;&#1103; &#1079;&#1072;&#1087;&#1080;&#1089;&#1091; &#1076;&#1080;&#1089;&#1082;&#1110;&#1074; Brasero
X-GNOME-FullName[vi]=Công c&#7909; chép ra &#273;&#297;a Brasero
X-GNOME-FullName[zh_CN]=Brasero &#20809;&#30424;&#21051;&#24405;&#22120;
X-GNOME-FullName[zh_HK]=Brasero &#20809;&#30879;&#29138;&#37636;&#31243;&#24335;
X-GNOME-FullName[zh_TW]=Brasero &#20809;&#30879;&#29138;&#37636;&#31243;&#24335;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=brasero
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.28.2
X-Ubuntu-Gettext-Domain=brasero

```

and
```
$ cat /usr/share/applications/brasero-nautilus.desktop
[Desktop Entry]
Name=CD/DVD Creator
Comment=Create CDs and DVDs
Categories=GNOME;GTK;Utility;
TryExec=nautilus
Exec=nautilus --no-default-window --no-desktop burn:/// 
Icon=brasero
MimeType=x-content/blank-cd;x-content/blank-dvd;x-content/blank-bd;x-content/blank-hddvd;
StartupNotify=true
Terminal=false
Type=Application
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=brasero
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.28.2
X-Ubuntu-Gettext-Domain=brasero

```

---

### Post by llakais on 2010-06-10
Hey, thanks for the response!

So, do you think it's okay if I delete the extra .desktop files from /usr/share/applications?  Or will that mess with functionality?

---

### Post by bcbc on 2010-06-10
> **llakais said:**
> Hey, thanks for the response!

So, do you think it's okay if I delete the extra .desktop files from /usr/share/applications?  Or will that mess with functionality?

No idea... my gut says it would be fine, but I've seen a lot people on the forums who followed their gut and it lied :)

---

### Post by llakais on 2010-06-11
Haha, well, I'll just keep it in the back of my head as an option in case the problem gets worse and I really want to fix it.

Thanks a ton for your help, man!

---

### Post by bcbc on 2010-06-11
You're welcome... 

since i have my 'development' version running right now (which I expect to break at any time anyway) I tried it. Nothing bad happened.

I deleted the first brasero.desktop
```
$ cd /usr/share/application
$ sudo cp brasero.desktop ~/brasero.desktop
$ sudo rm brasero.desktop

```
Now only one shows up. Again, no idea about the difference in functionality between the two and what consequence this will bring.

You can run the diff command to see what the differences are:
```
$ diff brasero-nautilus.desktop brasero.desktop 
2,8c2,8
< Name=CD/DVD Creator
< Comment=Create CDs and DVDs
< Categories=GNOME;GTK;Utility;
< TryExec=nautilus
< Exec=nautilus --no-default-window --no-desktop burn:/// 
< Icon=system-file-manager
< MimeType=x-content/blank-cd;x-content/blank-dvd;x-content/blank-bd;x-content/blank-hddvd;
---
> Name=Brasero
> GenericName=Disc Burner
> Comment=Create and copy CDs and DVDs
> Categories=GNOME;AudioVideo;DiscBurning;
> MimeType=application/x-cd-image;application/x-cdrdao-toc;application/x-cue;application/x-toc;audio/x-scpls;audio/x-ms-asx;audio/x-mp3-playlist;audio/x-mpegurl;application/x-brasero;
> Exec=brasero %U
> Icon=brasero
12c12
< OnlyShowIn=GNOME;
---
> X-GNOME-FullName=Brasero Disc Burner

```

---

### Post by llakais on 2010-06-12
Well, I went for it and I've since tested out lots of the programs that might've been affected and everything seems to be running a-ok.  Opening files using the "open with" menu works great, too.

I guess I won't know for sure unless something eventually breaks, but it seems to me like deleting the extra .desktop files did the trick, so I'll mark this as solved.

Thanks for bearing with me, bcbc!

---

### Post by afrodeity on 2010-11-17
Gnome seriously needs a better "open with" browser. The one on OSX really puts the Gnome-Nautilus combo to shame.

---

