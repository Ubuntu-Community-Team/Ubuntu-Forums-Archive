---
title: "how ot mount hard drives at startup"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by gkraju on 2009-02-25
i have 5 partitions in my system 
when i login to system each time i hav to mount manually all the drives
is their any way i can mount automatically all the drives at startup ?
thanks in advance

---

### Post by taurus on 2009-02-25
If you want them to be mounted automatically each time you boot, you need to create 5 new entries (one for each partition) in /etc/fstab.  What filesystems are those partitions?

Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by llamabr on 2009-02-25
You should look into editing your /etc/fstab.

Notice that I did not tell you to read the man page for fstab, but rather, to look into it.

In fact, if, when they're all mounted, you send us the output of df we'll even do it for you.

---

### Post by gkraju on 2009-02-26
> **llamabr said:**
> You should look into editing your /etc/fstab.

Notice that I did not tell you to read the man page for fstab, but rather, to look into it.

In fact, if, when they're all mounted, you send us the output of df we'll even do it for you.

this is printed 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18371836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda5            3825        6355    20330226    b  W95 FAT32
/dev/sda6            8957       11472    20209738+   b  W95 FAT32
/dev/sda7           11473       15296    30716248+   b  W95 FAT32
/dev/sda8           15297       17289    16008741    7  HPFS/NTFS
/dev/sda9           17290       19456    17406396    7  HPFS/NTFS
/dev/sda10           6356        8956    20892501    7  HPFS/NTFS

Partition table entries are not in disk order

---

### Post by taurus on 2009-02-26
> **gkraju said:**
> this is printed 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18371836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda5            3825        6355    20330226    b  W95 FAT32
/dev/sda6            8957       11472    20209738+   b  W95 FAT32
/dev/sda7           11473       15296    30716248+   b  W95 FAT32
/dev/sda8           15297       17289    16008741    7  HPFS/NTFS
/dev/sda9           17290       19456    17406396    7  HPFS/NTFS
/dev/sda10           6356        8956    20892501    7  HPFS/NTFS

Partition table entries are not in disk order

So you want to mount all those 7 partitions, 3 vfat and 4 ntfs.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these lines to the end of it.

```

/dev/sda5   /media/sda5   vfat   iocharset=utf8,umask=000  0  0
/dev/sda6   /media/sda6   vfat   iocharset=utf8,umask=000  0  0
/dev/sda7   /media/sda7   vfat   iocharset=utf8,umask=000  0  0
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda8   /media/sda8   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda9   /media/sda9   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda10  /media/sda10  ntfs-3g  defaults,locale=**en_US**.UTF-8  0  0

```
Assuming you are in the US.  

Save it and close down gedit editing window.  Now, create those new mount points and mount them.

```
sudo mkdir /media/sda1 /media/sda5 /media/sda6 /media/sda7 /media/sda8 /media/sda9 /media/sda10
sudo mount -a 
df -h
```

---

### Post by gkraju on 2009-02-26
> **taurus said:**
> So you want to mount all those 7 partitions, 3 vfat and 4 ntfs.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these lines to the end of it.

```

/dev/sda5   /media/sda5   vfat   iocharset=utf8,umask=000  0  0
/dev/sda6   /media/sda6   vfat   iocharset=utf8,umask=000  0  0
/dev/sda7   /media/sda7   vfat   iocharset=utf8,umask=000  0  0
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda8   /media/sda8   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda9   /media/sda9   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda10  /media/sda10  ntfs-3g  defaults,locale=**en_US**.UTF-8  0  0

```
Assuming you are in the US.  

Save it and close down gedit editing window.  Now, create those new mount points and mount them.

```
sudo mkdir /media/sda1 /media/sda5 /media/sda6 /media/sda7 /media/sda8 /media/sda9 /media/sda10
sudo mount -a 
df -h
```

i am in india what i have to add for that en_US or where i have to find it

---

### Post by tarps87 on 2009-02-26
Hopefully this will help:
[http://download1.swsoft.com/Plesk/Plesk8.1/Doc/plesk-8.1-win-l10n-guide/39382.htm](http://download1.swsoft.com/Plesk/Plesk8.1/Doc/plesk-8.1-win-l10n-guide/39382.htm)

This will list all the local types available on you computer
```
locale -a
```

---

### Post by taurus on 2009-02-26
If you are using the English, I believe you would use en_IN.  Otherwise, here is the list of all the locales (or at least most of them).

```

Locales

af_ZA Afrikaans locale for South Africa
am_ET Amharic language locale for Ethiopia
ar_AE Arabic language locale for United Arab Emirates
ar_BH Arabic language locale for Bahrein
ar_DZ Arabic language locale for Algeria
ar_EG Arabic language locale for Egypt
**ar_IN Arabic language locale for India**
ar_IQ Arabic language locale for Iraq
ar_JO Arabic language locale for Jordan
ar_KW Arabic language locale for Kuwait
ar_LB Arabic language locale for Lebanon
ar_LY Arabic language locale for Libyan Arab Jamahiriya
ar_MA Arabic language locale for Morocco
ar_OM Arabic language locale for Oman
ar_QA Arabic language locale for Qatar
ar_SA Arabic locale for Saudi Arabia
ar_SD Arabic language locale for Sudan
ar_SY Arabic language locale for Syrian Arab Republic
ar_TN Arabic language locale for Tunisia
ar_YE Arabic language locale for Yemen
az_AZ Azeri language locale for Azerbaijan (latin)
be_BY Belarusian locale for Belarus
bg_BG Bulgarian locale for Bulgaria
**bn_IN Bengali language locale for India**
br_FR Breton language locale for France
bs_BA Bosnian language locale for Bosnia and Herzegowina
ca_ES Catalan locale for Catalonia
cs_CZ Czech locale for the Czech Republic
cy_GB Welsh language locale for Great Britain
da_DK Danish locale for Denmark
de_AT German locale for Austria
de_BE German locale for Belgium
de_CH German locale for Switzerland
de_DE German locale for Germany
de_LU German locale for Luxemburg
el_GR Greek locale for Greece
en_AU English locale for Australia
en_BW English locale for Botswana
en_CA English locale for Canada
en_DK English locale for Denmark
en_GB English locale for Britain
en_HK English locale for Hong Kong
en_IE English locale for Ireland
en_IN English language locale for India
en_NZ English locale for New Zealand
en_PH English language locale for Philippines
en_SG English language locale for Singapore
en_US English locale for the USA
en_ZA English locale for South Africa
en_ZW English locale for Zimbabwe
eo_EO Esperanto locale
es_AR Spanish locale for Argentina
es_BO Spanish locale for Bolivia
es_CL Spanish locale for Chile
es_CO Spanish locale for Colombia
es_CR Spanish locale for Costa Rica
es_DO Spanish locale for Dominican Republic
es_EC Spanish locale for Equador
es_ES Spanish locale for Spain
es_GT Spanish locale for Guatemala
es_HN Spanish locale for Honduras
es_MX Spanish locale for Mexico
es_NI Spanish locale for Nicaragua
es_PA Spanish locale for Panama
es_PE Spanish locale for Peru
es_PR Spanish locale for Puerto Rico
es_PY Spanish locale for Paraguay
es_SV Spanish locale for El Salvador
es_US Spanish locale for the USA
es_UY Spanish locale for Uruguay
es_VE Spanish locale for Venezuela
et_EE Estonian locale for Estonia
eu_ES Basque locale for Spain
fa_IR Persian locale for Iran
fi_FI Finnish locale for Finland
fo_FO Faroese locale for Faroe Islands
fr_BE French locale for Belgium
fr_CA French locale for Canada
fr_CH French locale for Switzerland
fr_FR French locale for France
fr_LU French locale for Luxemburg
ga_IE Irish locale for Ireland
gd_GB Scots Gaelic language locale for Great Britain
gl_ES Galician locale for Spain
gv_GB Manx Gaelic locale for Britain
he_IL Hebrew locale for Israel
**hi_IN Hindi language locale for India**
hr_HR Croatian locale for Croatia
hu_HU Hungarian locale for Hungary
hy_AM Armenian language locale for Armenia
id_ID Indonesian locale for Indonesia
is_IS Icelandic locale for Iceland
it_CH Italian locale for Switzerland
it_IT Italian locale for Italy
iw_IL Hebrew locale for Israel
ja_JP Japanese language locale for Japan
ka_GE Georgian language locale for Georgia
kl_GL Greenlandic locale for Greenland
ko_KR Korean locale for Republic of Korea
kw_GB Cornish locale for Britain
lt_LT Lithuanian locale for Lithuania
lv_LV Latvian locale for Latvia
mi_NZ Maori language locale for New Zealand
mk_MK Macedonian locale for Macedonia
mr_IN Marathi language locale for India
ms_MY Malay language locale for Malaysia
mt_MT Maltese language locale for Malta
nl_BE Dutch locale for Belgium
nl_NL Dutch locale for the Netherlands
nn_NO Nynorsk language locale for Norway
no_NO Norwegian locale for Norway
oc_FR Occitan Language Locale for France
pl_PL Polish locale for Poland
pt_BR Portuguese locale for Brasil
pt_PT Portuguese locale for Portugal
ro_RO Romanian locale for Romania
ru_RU Russian locale for Russia
ru_UA Russian locale for Ukraine
se_NO Northern Saami language locale for Norway
sk_SK Slovak locale for Slovak
sl_SI Slovenian locale for Slovenia
sq_AL Albanian language locale for Albania
sr_YU Serbian locale for Yugoslavia
sv_FI Swedish locale for Finland
sv_SE Swedish locale for Sweden
[B]ta_IN Tamil language locale for India
te_IN Telgu language locale for India[/B]
tg_TJ Tajik language locale for Tajikistan
th_TH Thai locale for Thailand
ti_ER Tigrigna language locale for Eritrea
ti_ET Tigrigna language locale for Ethiopia
tl_PH Tagalog language locale for Philipines
tr_TR Turkish locale for Turkey map
tt_RU Tatar language locale for Tatarstan
uk_UA Ukrainian locale for Ukraine
ur_PK Urdu Language Locale for Pakistan
uz_UZ Uzbek locale for Uzbekistan
vi_VN Vietnamese language locale for Vietnam
wa_BE Walloon Language Locale for Belgium
yi_US Yiddish Language locale
zh_CN Chinese locale for Peoples Republic of China
zh_HK Chinese language locale for Hong Kong
zh_SG Chinese language locale for Singapore
zh_TW Chinese locale for Taiwan R.O.C.

```

---

### Post by YesSir on 2009-02-26
For me, checking "remember authorization" at mounting worked:

[http://www.psychocats.net/ubuntu/images/mountwindows01.png](http://www.psychocats.net/ubuntu/images/mountwindows01.png)

Never had to mount ever since.

---

### Post by myddewji13 on 2009-02-26
if they are ntfs partitions then try ntfs config tool in add/remove..

---

### Post by Si_M on 2009-03-01
I am having much the same problem also I would like to maintain the same drive letters at start up.

My fstab info is 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1cc3a131-4132-46fc-81db-63b261d4986b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=486ed596-7cbc-4386-9a33-3874850a9f55 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by taurus on 2009-03-01
> **Si_M said:**
> I am having much the same problem also I would like to maintain the same drive letters at start up.

My fstab info is 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1cc3a131-4132-46fc-81db-63b261d4986b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=486ed596-7cbc-4386-9a33-3874850a9f55 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Do you want your windows partition automatically mounts each time you boot Ubuntu?  Then can you also post the output of this command.

```
sudo fdisk -l
```

And if it is ntfs, then use ntfs-config to configure it.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by Si_M on 2009-03-01
> **taurus said:**
> Do you want your windows partition automatically mounts each time you boot Ubuntu?  Then can you also post the output of this command.

```
sudo fdisk -l
```

And if it is ntfs, then use ntfs-config to configure it.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```


There shouldn't be a windows partition, unless it's suse?

---

### Post by Si_M on 2009-03-01
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c633c62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9380    75344818+  83  Linux
/dev/sda2            9381        9733     2835472+   5  Extended
/dev/sda5            9381        9733     2835441   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000157a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1946    15631213+  83  Linux
/dev/sdb2            1947        4866    23454900   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3fe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    b  W95 FAT32

---

### Post by taurus on 2009-03-01
So you want to mount SUSE partition.  Can you post the outputs of these commands from a terminal?

```

sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Si_M on 2009-03-01
Thanks taurus

thinking about it I don't really need to mount that I just need access to the 500gb drive if you can help there.

Thanks

---

### Post by taurus on 2009-03-01
```
sudo mkdir /media/sdc1
sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
df -h
```

---

### Post by Si_M on 2009-03-01
> **taurus said:**
> ```
sudo mkdir /media/sdc1
sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  4.4G   63G   7% /
varrun                474M  224K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   68K  474M   1% /dev
devshm                474M   12K  474M   1% /dev/shm
lrm                   474M   39M  435M   9% /lib/modules/2.6.24-23-generic/volatile
/dev/sdb2              23G  279M   21G   2% /media/disk-1
/dev/sdb1              15G  3.2G   11G  23% /media/disk-2
/dev/sdc1             466G  389G   78G  84% /media/sdc1

---

### Post by taurus on 2009-03-01
> **Si_M said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  4.4G   63G   7% /
varrun                474M  224K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   68K  474M   1% /dev
devshm                474M   12K  474M   1% /dev/shm
lrm                   474M   39M  435M   9% /lib/modules/2.6.24-23-generic/volatile
/dev/sdb2              23G  279M   21G   2% /media/disk-1
/dev/sdb1              15G  3.2G   11G  23% /media/disk-2
**[COLOR="Blue"]/dev/sdc1             466G  389G   78G  84% /media/sdc1[/COLOR]**

There you go.

```
ls -la /media/sdc1
```

---

### Post by Si_M on 2009-03-01
> **taurus said:**
> There you go.

```
ls -la /media/sdc1
```

Is that it then all I have to do? Will it now open automatically?

Thanks Taurus

---

### Post by taurus on 2009-03-01
If you want /dev/sdc1 to mount automatically each time you boot Ubuntu, then you need to add an entry in /etc/fstab for it.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdc1   /media/sdc1   vfat   iocharset=utf8,umask=000  0  0
```
Save it and reboot.

---

