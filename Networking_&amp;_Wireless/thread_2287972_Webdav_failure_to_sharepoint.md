---
title: "Webdav failure to sharepoint"
date: 2015-07-23
forum: Networking &amp; Wireless
---

### Post by Jonathan L on 2015-07-23
Hello 

I'm trying to connect from Ubuntu server to a sharepoint server (for the purpose of exporting everything from sharepoint so I can switch it off!).

```
$** sudo mount -t davfs -o ro http://sharepoint.example.com /media/sharepoint**
Please enter the username to authenticate with server
http://sharepoint.example.com or hit enter for none.
  Username: jonathanl
Please enter the password to authenticate user jonathanl with server
http://sharepoint.example.com or hit enter for none.
  Password:
/sbin/mount.davfs: Mounting failed.
[COLOR=#ff0000]Could not authenticate to server: ignored NTLM challenge, GSSAPI authentication error: Unspecified GSS failure.  Minor code may provide more information: No Kerberos credentials available[/COLOR]
```[COLOR=#ff0000]
[/COLOR]
Any thoughts on what that can be?  I've been chasing it for some time now.

Ubuntu 14.04 details below;  sharepoint server is Sharepoint 2010 Foundation on Windows 2008 R2 Standard 64 Bit; it mounts over webdav perfectly from Windows 7 with the same credentials.

Any tips or suggestions gratefully received.

Thanks,
Jonathan.

```
$ **uname -a**
Linux scruffy 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ **lsb_release -a**
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

$ **lsmod**
Module                  Size  Used by
coda                   41734  0
arc4                   12608  0
md4                    12595  0
nls_utf8               12557  2
cifs                  462689  3
fscache                63988  1 cifs
nfnetlink              14606  0
bluetooth             391196  0
ppdev                  17671  0
coretemp               13435  0
crct10dif_pclmul       14289  0
crc32_pclmul           13113  0
ghash_clmulni_intel    13216  0
aesni_intel            55624  0
vmw_balloon            13415  0
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13462  0
vmwgfx                175358  1
ttm                    85115  1 vmwgfx
drm                   303102  2 ttm,vmwgfx
i2c_piix4              22155  0
vmw_vmci               62966  0
shpchp                 37032  0
parport_pc             32701  1
mac_hid                13205  0
lp                     17759  0
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0
mptspi                 22542  2
vmxnet3                49693  0
mptscsih               40150  1 mptspi
mptbase               101822  2 mptspi,mptscsih
floppy                 69418  0
```

---

