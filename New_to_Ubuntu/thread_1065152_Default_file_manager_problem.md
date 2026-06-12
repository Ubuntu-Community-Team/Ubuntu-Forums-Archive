---
title: "Default file manager problem"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by photolinux on 2009-02-09
I am running Ubuntu 8.10. For some reason my default file manager is Dolphin. 

How would I proceed to switch my default file manager back to nautilus?

---

### Post by joey-elijah on 2009-02-09
Are you using the Gnome desktop? lol Just gotta check!

I imagine just sudo apt-get install nautilus and then follow the guides here to set it as default: -

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by photolinux on 2009-02-19
> Are you using the Gnome desktop? lol Just gotta check!

I imagine just sudo apt-get install nautilus and then follow the guides here to set it as default: -

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

I am using the Gnome desktop, and there is no other desktop environment installed. This makes me wonder how my default file manager changed?

I ran the script and rebooted, however there is no change.
```

*@*-desktop:~/Desktop$ ./restorenautilus.sh 

You're missing a Computer .desktop backup file--nothing to restore


You're missing a Nautilus .desktop backup file--nothing to restore


You're missing a folder handler .desktop backup file--nothing to restore


You're missing a Home .desktop backup file--nothing to restore


You're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.


Nautilus should now be your new default file manager in Gnome again
```

---

### Post by gackt on 2009-02-20
hmmmm i dont know. but will this help "right click folder open with and enter the desired explorer"

---

### Post by joshzam on 2009-02-21
You may have to edit this config file:

```
gksu gedit /usr/share/applications/nautilus-folder-handler.desktop
```

Look for a line that reads ```
Exec=nautilus --no-desktop %U
```

I know that when I switched my default file manager from Nautilus to Thunar, I had to replace this line with ```
Exec=thunar %U
```

You're gonna wanna make sure Nautilus is mentioned in this file.

If you make a change, save the file, log out and back in again, and test the changes by selecting Places > Home.

---

### Post by photolinux on 2009-02-24
>  	
Re: Default file manager problem
You may have to edit this config file:

Code:

gksu gedit /usr/share/applications/nautilus-folder-handler.desktop

Look for a line that reads
Code:

Exec=nautilus --no-desktop %U

I know that when I switched my default file manager from Nautilus to Thunar, I had to replace this line with
Code:

Exec=thunar %U

You're gonna wanna make sure Nautilus is mentioned in this file.

If you make a change, save the file, log out and back in again, and test the changes by selecting Places > Home. 



```
[Desktop Entry]
Encoding=UTF-8
Name=Open Folder
Name[af]=Open gids
Name[ar]=&#1575;&#1601;&#1578;&#1581; &#1575;&#1604;&#1605;&#1580;&#1604;&#1617;&#1583;
Name[as]=&#2475;&#2507;&#2482;&#2509;&#2465;&#2494;&#2544; &#2454;&#2497;&#2482;&#2497;&#2472;
Name[be]=&#1040;&#1076;&#1082;&#1088;&#1099;&#1094;&#1100; &#1090;&#1101;&#1095;&#1082;&#1091;
Name[be@latin]=Ad&#269;yni kataloh
Name[bg]=&#1054;&#1090;&#1074;&#1072;&#1088;&#1103;&#1085;&#1077; &#1085;&#1072; &#1087;&#1072;&#1087;&#1082;&#1072;
Name[bn_IN]=&#2475;&#2507;&#2482;&#2509;&#2465;&#2494;&#2480; &#2454;&#2497;&#2482;&#2497;&#2472;
Name[ca]=Obre la carpeta
Name[ca@valencia]=Obri la carpeta
Name[cs]=Otev&#345;ít složku
Name[da]=Åbn mappe
Name[de]=Ordner öffnen
Name[dz]=&#3942;&#4003;&#3964;&#3921;&#3851;&#3936;&#3931;&#3954;&#3923;&#3851;&#3905;&#3851;&#3925;&#4017;&#3962;&#3853;
Name[el]=&#902;&#957;&#959;&#953;&#947;&#956;&#945; &#966;&#945;&#954;&#941;&#955;&#959;&#965;
Name[en_CA]=Open Folder
Name[en_GB]=Open Folder
Name[eo]=Malfermu dosierujon
Name[es]=Abrir carpeta
Name[et]=Avatakse kataloog
Name[eu]=Ireki karpeta
Name[fi]=Avaa kansio
Name[fr]=Ouvrir le dossier
Name[fur]=Vierç cartele
Name[ga]=Oscail Fillteán
Name[gl]=Abrir cartafol
Name[gu]=&#2731;&#2763;&#2738;&#2765;&#2721;&#2736; &#2710;&#2763;&#2738;&#2763;
Name[he]=&#1508;&#1514;&#1495; &#1514;&#1497;&#1511;&#1497;&#1497;&#1492;
Name[hi]=&#2326;&#2369;&#2354;&#2366; &#2347;&#2364;&#2379;&#2354;&#2381;&#2337;&#2352;
Name[hr]=Otvori mapu
Name[hu]=Mappa megnyitása
Name[id]=Buka Folder
Name[io]=Apertez Dokumentuyo
Name[it]=Apri cartella
Name[ja]=&#12501;&#12457;&#12523;&#12480;&#12434;&#38283;&#12367;
Name[ka]=&#4307;&#4304;&#4321;&#4322;&#4312;&#4321; &#4306;&#4304;&#4334;&#4321;&#4316;&#4304;
Name[kn]=&#3221;&#3233;&#3236;&#3221;&#3275;&#3254;&#3253;&#3240;&#3277;&#3240;&#3265; &#3236;&#3270;&#3248;&#3270;
Name[ko]=&#54260;&#45908; &#50676;&#44592;
Name[ku]=Peldankê Veke
Name[lt]=Atverti aplank&#261;
Name[lv]=Atv&#275;rt mapi
Name[mk]=&#1054;&#1090;&#1074;&#1086;&#1088;&#1080; &#1076;&#1072;&#1090;&#1086;&#1090;&#1077;&#1082;&#1072;
Name[ml]=&#3333;&#3377; &#3364;&#3393;&#3377;&#3349;&#3405;&#3349;&#3393;&#3349; 
Name[mr]=&#2360;&#2306;&#2330;&#2351;&#2368;&#2325;&#2366; &#2313;&#2328;&#2337;&#2366;
Name[nb]=Åpne mappe
Name[ne]=&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2326;&#2379;&#2354;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381;
Name[nl]=Map openen
Name[nn]=Opna mappe
Name[oc]=Dobrir un repertòri
Name[pa]=&#2603;&#2635;&#2610;&#2593;&#2608; &#2582;&#2635;&#2610;&#2637;&#2617;&#2635;
Name[pl]=Otwórz katalog
Name[ps]=&#1662;&#1608;&#1690;&#1741; &#1662;&#1585;&#1575;&#1606;&#1610;&#1587;&#1578;&#1604;
Name[pt]=Abrir Pasta
Name[pt_BR]=Abrir pasta
Name[ro]=Deschide dosarul
Name[ru]=&#1054;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1087;&#1072;&#1087;&#1082;&#1091;
Name[si]=&#3510;&#3524;&#3517;&#3540;&#3512; &#3520;&#3538;&#3520;&#3544;&#3501; &#3482;&#3515;&#3505;&#3530;&#3505;
Name[sk]=Otvori&#357; prie&#269;inok
Name[sl]=Odpri mapo
Name[sq]=Hap kartelën
Name[sr]=&#1054;&#1090;&#1074;&#1086;&#1088;&#1080; &#1092;&#1072;&#1089;&#1094;&#1080;&#1082;&#1083;&#1091;
Name[sr@latin]=Otvori fasciklu
Name[sv]=Öppna mapp
Name[ta]=&#2949;&#2975;&#3016;&#2997;&#3007;&#2985;&#3016; &#2980;&#3007;&#2993;
Name[te]=&#3128;&#3074;&#3098;&#3119;&#3134;&#3112;&#3149;&#3112;&#3135; &#3108;&#3142;&#3120;&#3137;&#3125;&#3137;&#3118;&#3137;
Name[th]=&#3648;&#3611;&#3636;&#3604;&#3650;&#3615;&#3621;&#3648;&#3604;&#3629;&#3619;&#3660;
Name[tr]=Klasör Aç
Name[uk]=&#1044;&#1086;&#1084;&#1072;&#1096;&#1085;&#1103; &#1090;&#1077;&#1082;&#1072;
Name[vi]=M&#7903; th&#432; m&#7909;c
Name[zh_CN]=&#25171;&#24320;&#25991;&#20214;&#22841;
Name[zh_HK]=&#38283;&#21855;&#36039;&#26009;&#22846;
Name[zh_TW]=&#38283;&#21855;&#36039;&#26009;&#22846;
TryExec=nautilus
**Exec=nautilus --no-desktop %U**
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.24.1
X-Ubuntu-Gettext-Domain=nautilus
```
It seems it is set to Nautilus. 
Are there any other configuration files I can check?

---

### Post by patrickaupperle on 2009-03-24
I am having the same problem, Please someone, help us solve it.

---

### Post by patrickaupperle on 2009-03-24
Just found something, trying it now. 
From ArchWiki:
> If you want to do everything manually, create /usr/share/applications/defaults.list with the following format:
```
[Default Applications]
application/pdf=evince.desktop
image/jpeg=eog.desktop
...
```

---

