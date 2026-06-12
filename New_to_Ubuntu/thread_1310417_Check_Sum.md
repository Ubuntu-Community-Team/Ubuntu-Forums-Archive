---
title: "Check Sum"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by ibbill on 2009-11-01
Hi [HERE ]("http://releases.ubuntu.com/9.10/")is where I am downloading the 9.10 from on this page.

This is the one I am downloading (PC (Intel x86) desktop CD) can anyone tell me what the checksum number is please.

Bill

---

### Post by Rhubarb on 2009-11-01
The checksum MD5s can be found here:
[http://releases.ubuntu.com/9.10/MD5SUMS](http://releases.ubuntu.com/9.10/MD5SUMS)

> 836440698456aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
d91659de6e945dbb96eb8970b2b4590a *ubuntu-9.10-desktop-armel+dove.img
297875d2a7531824a0fb08f241d33e85 *ubuntu-9.10-desktop-armel+imx51.img
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
ed6e77587b87fe0d92a2f21855869f00 *ubuntu-9.10-netbook-remix-i386.iso
14707e8847b9c9ba2dd1869fb5086e4f *ubuntu-9.10-server-amd64.iso
55618ad5f180692f9dac20cbff352634 *ubuntu-9.10-server-i386.iso
37a04db193b1a342f961f59aea2fada8 *wubi.exe


It's always good to check your downloads are correct before you go to burn them / transfer them to USB :)

---

### Post by peculiar penguin on 2009-11-01
They're linked at the bottom of that page:
[http://releases.ubuntu.com/9.10/MD5SUMS](http://releases.ubuntu.com/9.10/MD5SUMS)
[http://releases.ubuntu.com/9.10/SHA1SUMS](http://releases.ubuntu.com/9.10/SHA1SUMS)
[http://releases.ubuntu.com/9.10/SHA256SUMS](http://releases.ubuntu.com/9.10/SHA256SUMS)

So in your case the MD5 checksum should be 8790491bfa9d00f283ed9dd2d77b3906, for example.

---

### Post by ibbill on 2009-11-01
Thanks for your help I posted everyone of the numbers you showed and the only match I received was 

37a04db193b1a342f961f59aea2fada8 *wubi.exe 

I opened the disk I downloaded and clicked on the md5sum,tx and opened it with gedit have attached a file for you to see am i missing something here if so I apologize thanks 
oops no file will try again.

Bill

---

### Post by ibbill on 2009-11-01
sorry this is what is on the disk under checksum


f74d16c6b6e4d182e009a50898df7761  ./casper/initrd.lz
fa96b9b7ef0103fbe80689c87788307c  ./casper/filesystem.manifest
c75ae10fb8074945a616dcf944134e45  ./casper/filesystem.manifest-desktop
71b1d98e4f8357f25946dc1eccd42c05  ./casper/filesystem.squashfs
284af6e5e36cc3cd8c096b00ad4a3f96  ./casper/vmlinuz
1b955c5153cb8d145125f817823cca33  ./dists/karmic/Release
93a20440cf0c7d4a21d1eed1f0466005  ./dists/karmic/restricted/binary-i386/Packages.gz
a2b3e2dbeb3eaa7aac0d0d9d20aac0ac  ./dists/karmic/restricted/binary-i386/Release
f31a503c27165eceb99fd1a937d72abe  ./dists/karmic/Release.gpg
608213e5def52f3beeed331670771bd0  ./dists/karmic/main/binary-i386/Packages.gz
eebfac7a31cdc0c22af95dd6330ca2d5  ./dists/karmic/main/binary-i386/Release
461cbc7ff94fdea8008cab34b611abb8  ./pics/blue-upperright.png
cd8aa5e7fa11b1362ef1869ac6b1aa56  ./pics/blue-lowerleft.png
a025c46d5daf227adfda51d81eb90f25  ./pics/blue-upperleft.png
92091902d3ca753bb858d4682b3fc26b  ./pics/logo-50.jpg
3c129ee10f707bd9dec10209d28840eb  ./pics/red-upperright.png
cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png
20d4bdecfa6d980d663fb5b93d37a842  ./pics/red-lowerright.png
0730e775a72519aaa450a3774fca5f55  ./pics/red-lowerleft.png
16ff51c168405e575d32bae001f280e4  ./pics/debian.jpg
9e18ae797773b2677b1b7b86e2aff28d  ./pics/blue-lowerright.png
7d78d675fc0e05d5d34c49c8fc851b1d  ./.disk/casper-uuid-generic
264a112e2a88b1cc96d30bae564874dc  ./.disk/release_notes_url
728cb968a88534e0c50a9d99621f13eb  ./.disk/cd_type
d41d8cd98f00b204e9800998ecf8427e  ./.disk/base_installable
9fa2d8c991e62f5e86110bcd570b5051  ./.disk/info
62bf7841341b7faa69062fd0095af116  ./autorun.inf
8d6a2a045d7c0f48fe2e088f3f87b6ce  ./install/README.sbm
5a93a111efeb5305075c5e077715b6cd  ./install/sbm.bin
5393cf82120c63adf4f21b5060274f2a  ./install/mt86plus
d007768a1066ab1419d93daea54c4844  ./preseed/ubuntu.seed
a4b29b43f9757c3a69528db02c8e6dd4  ./preseed/ltsp.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
fc3e7d4d12a10c07c84e5f5c09ad88a2  ./pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
ff775ab4bde94e945e235cfa8f5b1ada  ./pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20080817-3ubuntu3_i386.deb
4fdb13bd00fb191e6301216d1e1a2a2f  ./pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb
ce92bed373978042b9561570e7806258  ./pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb
7d2f89b3676823a4105e47d10c282986  ./pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb
e440a1267b16d77c20208a9ca03501d6  ./pool/main/b/build-essential/build-essential_11.4_i386.deb
84b0083eb828801c2c75db44d12f238d  ./pool/main/b/b43-fwcutter/b43-fwcutter_012-1_i386.deb
7a19ad9ee0b474c8f5782b3bd42380c4  ./pool/main/d/dpkg/dpkg-dev_1.15.4ubuntu2_all.deb
ca5ff1788057e323d8def0696abba11b  ./pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb
1c23ace9ad8dc6ea4b6f75c0dafcc83f  ./pool/main/g/gcc-4.4/g++-4.4_4.4.1-4ubuntu8_i386.deb
005ba5cc29a46a5932d5157e4048d070  ./pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.1-4ubuntu8_i386.deb
358d5397044b460835cc2821a58dfa2d  ./pool/main/g/gcc-defaults/g++_4.4.1-1ubuntu2_i386.deb
2b3503ba81cd74be547b4706e131147b  ./pool/main/u/ubiquity/oem-config_2.0.8_all.deb
fd80d0cc879ac1168af2a3aedd7b4527  ./pool/main/u/ubiquity/oem-config-gtk_2.0.8_all.deb
96eb932ca49e014530b536d4d281ebff  ./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu4_i386.deb
1dd9db50e158d3bc57cd03ddbd0b02bc  ./pool/main/f/fakeroot/fakeroot_1.12.4ubuntu1_i386.deb
590457a006ef013f74565c15d2bc78e0  ./pool/main/p/pptp-linux/pptp-linux_1.7.2-3_i386.deb
b3d1fec95d04d924a08886e601bd1d46  ./pool/main/p/patch/patch_2.5.9-5_i386.deb
60e54d2e2c75f9bc8e64ac7311bd1d8e  ./pool/main/l/linux-wlan-ng/linux-wlan-ng-doc_0.2.9+dfsg-2ubuntu2_all.deb
4e45d98a06336b6554317db875f8c747  ./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.9+dfsg-2ubuntu2_i386.deb
2e6e15c55a8c8c58c89f2c07cdd7b028  ./pool/main/l/lupin/lupin-support_0.27_all.deb
c2cd3b1c7e406f6bf2d4648df0073a2f  ./pool/main/s/setserial/setserial_2.17-45_i386.deb
37a04db193b1a342f961f59aea2fada8  ./wubi.exe
f2c70385776a5b043d67ebdc7e132014  ./README.diskdefines

---

### Post by ibbill on 2009-11-01
> **peculiar penguin said:**
> They're linked at the bottom of that page:
[http://releases.ubuntu.com/9.10/MD5SUMS](http://releases.ubuntu.com/9.10/MD5SUMS)
[http://releases.ubuntu.com/9.10/SHA1SUMS](http://releases.ubuntu.com/9.10/SHA1SUMS)
[http://releases.ubuntu.com/9.10/SHA256SUMS](http://releases.ubuntu.com/9.10/SHA256SUMS)

So in your case the MD5 checksum should be 8790491bfa9d00f283ed9dd2d77b3906, for example.

thanks that is what i thought was not sure and its not there in the file on the disk. Is this download corrupt then.
Bill

---

### Post by sandyd on 2009-11-01
> **ibbill said:**
> Thanks for your help I posted everyone of the numbers you showed and the only match I received was 

**37a04db193b1a342f961f59aea2fada8 *wubi.exe **

I opened the disk I downloaded and clicked on the md5sum,tx and opened it with gedit have attached a file for you to see am i missing something here if so I apologize thanks 
oops no file will try again.

Bill
yup. the md5s match. download is not corrupted.

---

### Post by ibbill on 2009-11-01
Carlee thanks for the help I still don't see the # or the match gasp. Can you tell me which one it is please. So I will know next time thanks again.

Bill

---

### Post by sandyd on 2009-11-01
> **ibbill said:**
> Carlee thanks for the help I still don't see the # or the match gasp. Can you tell me which one it is please. So I will know next time thanks again.

Bill
ubuntu only gives you the md5sum for wubi.exe, not the rest of the files.
so you test the md5sum of the wubi.exe file only and see if they match
**37a04db193b1a342f961f59aea2fada8** *wubi.exe

only the bolded portion matters.

---

### Post by ibbill on 2009-11-01
Thank you thank you slaps self in head and now I know.

Thank you ALL for being here and for all your help

Bill](*,)

---

