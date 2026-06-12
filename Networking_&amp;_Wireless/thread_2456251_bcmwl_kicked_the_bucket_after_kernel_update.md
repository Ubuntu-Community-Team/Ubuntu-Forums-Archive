---
title: "bcmwl kicked the bucket after kernel update"
date: 2021-01-07
forum: Networking &amp; Wireless
---

### Post by eZtaR on 2021-01-07
Yesterday i installed the kernel update via apt upgrade and since then my wifi hasn't been working.

Today i decided on reinstalling the driver offline via sudo dpkg --purge bcmwl-kernel-source, and then reinstalling via the following where i get this error:
```
mcenter@mcenter:~/Desktop$ sudo dpkg -i bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb 
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 191827 files and directories currently installed.)
Preparing to unpack bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 5.8.0-34-generic
Building for architecture x86_64
Building initial module for 5.8.0-34-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 5.8.0-34-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--install):
 installed bcmwl-kernel-source package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source

```


Inside the /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log is the following:
```
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.8.0-34-generic (x86_64)
Thu 07 Jan 2021 09:21:38 PM CET
make: Entering directory '/usr/src/linux-headers-5.8.0-34-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  AR      /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/built-in.a
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c: In function ‘osl_reg_map’:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:949:10: error: implicit declaration of function ‘ioremap_nocache’; did you mean ‘ioremap_cache’? [-Werror=implicit-function-declaration]
  949 |  return (ioremap_nocache((unsigned long)pa, (unsigned long)size));
      |          ^~~~~~~~~~~~~~~
      |          ioremap_cache
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:949:10: warning: returning ‘int’ from a function with return type ‘void *’ makes pointer from integer without a cast [-Wint-conversion]
  949 |  return (ioremap_nocache((unsigned long)pa, (unsigned long)size));
      |         ~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
make[1]: *** [scripts/Makefile.build:290: /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o] Error 1
make: *** [Makefile:1780: /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build] Error 2
make: Leaving directory '/usr/src/linux-headers-5.8.0-34-generic'
```

Any pointers at all much appreciated :)

---

### Post by #&amp;thj^% on 2021-01-07
The reason is obvious. Almost every time Canonical rolls out a HWE kernel, they forget to upgrade bcmwl-kernel-source in the repos.
[list]    [*]Remove all 5.8 kernel packages and also these meta packages:[/list]
```
    sudo apt remove --purge linux-generic-hwe-20.04
    sudo apt remove --purge linux-image-generic-hwe-20.04
    sudo apt remove --purge linux-headers-generic-hwe-20.04
```

Make sure that the linux-generic meta package is installed.

The second suggestion will keep the 5.4 major kernel version with normal security upgrades.

---

### Post by eZtaR on 2021-01-08
Thank you for the suggestion 1fallen, i ran the following commands
```
sudo apt install linux-generic
sudo apt remove --purge bcmwl-kernel-source linux-generic-hwe-20.04 linux-image-generic-hwe-20.04 linux-headers-generic-hwe-20.04

```

and the problem still persists, did i misunderstand your guidance? :)

Here's the output of /var/crash/bcmwl-kernel-source.0.crash , that's still giving me a warning every time i use apt, for good measure:
```
ProblemType: Package
DKMSBuildLog:
 DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.8.0-34-generic (x86_64)
 Wed 06 Jan 2021 09:50:32 PM CET
 make: Entering directory '/usr/src/linux-headers-5.8.0-34-generic'
 CFG80211 API is prefered for this kernel version
 Using CFG80211 API
   AR      /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/built-in.a
   CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
   CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o
   CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_iw.o
   CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c: In function &#8216;osl_reg_map&#8217;:
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:949:10: error: implicit declaration of function &#8216;ioremap_nocache&#8217;; did you mean &#8216;ioremap_cache&#8217;? [-Werror=implicit-function-declaration]
   949 |  return (ioremap_nocache((unsigned long)pa, (unsigned long)size));
       |          ^~~~~~~~~~~~~~~
       |          ioremap_cache
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:949:10: warning: returning &#8216;int&#8217; from a function with return type &#8216;void *&#8217; makes pointer from integer without a cast [-Wint-conversion]
   949 |  return (ioremap_nocache((unsigned long)pa, (unsigned long)size));
       |         ~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c: In function &#8216;wl_attach&#8217;:
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:593:20: error: implicit declaration of function &#8216;ioremap_nocache&#8217;; did you mean &#8216;ioremap_cache&#8217;? [-Werror=implicit-function-declaration]
   593 |  if ((wl->regsva = ioremap_nocache(dev->base_addr, PCI_BAR0_WINSZ)) == NULL) {
       |                    ^~~~~~~~~~~~~~~
       |                    ioremap_cache
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:593:18: warning: assignment to &#8216;void *&#8217; from &#8216;int&#8217; makes pointer from integer without a cast [-Wint-conversion]
   593 |  if ((wl->regsva = ioremap_nocache(dev->base_addr, PCI_BAR0_WINSZ)) == NULL) {
       |                  ^
 In file included from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:40:
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: In function &#8216;wl_set_auth_type&#8217;:
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.h:52:5: warning: this statement may fall through [-Wimplicit-fallthrough=]
    52 |  if (wl_dbg_level & WL_DBG_DBG) {   \
       |     ^
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:816:3: note: in expansion of macro &#8216;WL_DBG&#8217;
   816 |   WL_DBG(("network eap\n"));
       |   ^~~~~~
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:817:2: note: here
   817 |  default:
       |  ^~~~~~~
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c: In function &#8216;wl_pci_probe&#8217;:
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:780:2: warning: this &#8216;if&#8217; clause does not guard... [-Wmisleading-indentation]
   780 |  if ((val & 0x0000ff00) != 0)
       |  ^~
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:782:3: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the &#8216;if&#8217;
   782 |   bar1_size = pci_resource_len(pdev, 2);
       |   ^~~~~~~~~
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:783:15: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
   783 |   bar1_addr = (uchar *)ioremap_nocache(pci_resource_start(pdev, 2),
       |               ^
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c: In function &#8216;wl_reg_proc_entry&#8217;:
 /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:3376:58: error: passing argument 4 of &#8216;proc_create_data&#8217; from incompatible pointer type [-Werror=incompatible-pointer-types]
  3376 |  if ((wl->proc_entry = proc_create_data(tmp, 0644, NULL, &wl_fops, wl)) == NULL) {
       |                                                          ^~~~~~~~
       |                                                          |
       |                                                          const struct file_operations *
 In file included from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:38:
 ./include/linux/proc_fs.h:102:31: note: expected &#8216;const struct proc_ops *&#8217; but argument is of type &#8216;const struct file_operations *&#8217;
   102 | extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
       |                               ^~~~~~~~~~~~~~~~
 cc1: some warnings being treated as errors
 make[1]: *** [scripts/Makefile.build:288: /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o] Error 1
 make[1]: *** Waiting for unfinished jobs....
 cc1: some warnings being treated as errors
 make[1]: *** [scripts/Makefile.build:288: /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o] Error 1
 make: *** [Makefile:1780: /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build] Error 2
 make: Leaving directory '/usr/src/linux-headers-5.8.0-34-generic'
DKMSKernelVersion: 5.8.0-34-generic
Date: Wed Jan  6 21:50:35 2021
DuplicateSignature: dkms:bcmwl-kernel-source:6.30.223.271+bdcom-0ubuntu5:/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:949:10: error: implicit declaration of function &#8216;ioremap_nocache&#8217;; did you mean &#8216;ioremap_cache&#8217;? [-Werror=implicit-function-declaration]
Package: bcmwl-kernel-source 6.30.223.271+bdcom-0ubuntu5
PackageVersion: 6.30.223.271+bdcom-0ubuntu5
SourcePackage: bcmwl
Title: bcmwl-kernel-source 6.30.223.271+bdcom-0ubuntu5: bcmwl kernel module failed to build
ApportVersion: 2.20.11-0ubuntu27.14
Architecture: amd64
CasperMD5CheckResult: skip
Dependencies:
 adduser 3.118ubuntu2
 apt 2.0.2ubuntu0.2
 apt-utils 2.0.2ubuntu0.2
 binutils 2.34-6ubuntu1
 binutils-common 2.34-6ubuntu1
 binutils-x86-64-linux-gnu 2.34-6ubuntu1
 build-essential 12.8ubuntu1.1
 bzip2 1.0.8-2
 ca-certificates 20201027ubuntu0.20.04.1
 coreutils 8.30-3ubuntu2
 cpp 4:9.3.0-1ubuntu2
 cpp-9 9.3.0-17ubuntu1~20.04
 debconf 1.5.73
 debconf-i18n 1.5.73
 dirmngr 2.2.19-3ubuntu2
 distro-info-data 0.43ubuntu1.4
 dkms 2.8.1-5ubuntu1
 dpkg 1.19.7ubuntu3
 dpkg-dev 1.19.7ubuntu3
 fakeroot 1.24-1
 g++ 4:9.3.0-1ubuntu2
 g++-9 9.3.0-17ubuntu1~20.04
 gcc 4:9.3.0-1ubuntu2
 gcc-10-base 10.2.0-5ubuntu1~20.04
 gcc-9 9.3.0-17ubuntu1~20.04
 gcc-9-base 9.3.0-17ubuntu1~20.04
 gnupg 2.2.19-3ubuntu2
 gnupg-l10n 2.2.19-3ubuntu2
 gnupg-utils 2.2.19-3ubuntu2
 gpg 2.2.19-3ubuntu2
 gpg-agent 2.2.19-3ubuntu2
 gpg-wks-client 2.2.19-3ubuntu2
 gpg-wks-server 2.2.19-3ubuntu2
 gpgconf 2.2.19-3ubuntu2
 gpgsm 2.2.19-3ubuntu2
 gpgv 2.2.19-3ubuntu2
 init-system-helpers 1.57
 kmod 27-1ubuntu2
 libacl1 2.2.53-6
 libalgorithm-diff-perl 1.19.03-2
 libalgorithm-diff-xs-perl 0.04-6
 libalgorithm-merge-perl 0.08-3
 libapt-pkg6.0 2.0.2ubuntu0.2
 libasan5 9.3.0-17ubuntu1~20.04
 libasn1-8-heimdal 7.7.0+dfsg-1ubuntu1
 libassuan0 2.5.3-7ubuntu2
 libatomic1 10.2.0-5ubuntu1~20.04
 libattr1 1:2.4.48-5
 libaudit-common 1:2.8.5-2ubuntu6
 libaudit1 1:2.8.5-2ubuntu6
 libbinutils 2.34-6ubuntu1
 libbz2-1.0 1.0.8-2
 libc-dev-bin 2.31-0ubuntu9.1
 libc6 2.31-0ubuntu9.1
 libc6-dev 2.31-0ubuntu9.1
 libcap-ng0 0.7.9-2.1build1
 libcc1-0 10.2.0-5ubuntu1~20.04
 libcom-err2 1.45.5-2ubuntu1
 libcrypt-dev 1:4.4.10-10ubuntu4
 libcrypt1 1:4.4.10-10ubuntu4
 libctf-nobfd0 2.34-6ubuntu1
 libctf0 2.34-6ubuntu1
 libdb5.3 5.3.28+dfsg1-0.6ubuntu2
 libdpkg-perl 1.19.7ubuntu3
 libfakeroot 1.24-1
 libffi7 3.3-4
 libfile-fcntllock-perl 0.22-3build4
 libgcc-9-dev 9.3.0-17ubuntu1~20.04
 libgcc-s1 10.2.0-5ubuntu1~20.04
 libgcrypt20 1.8.5-5ubuntu1
 libgdbm-compat4 1.18.1-5
 libgdbm6 1.18.1-5
 libgmp10 2:6.2.0+dfsg-4
 libgnutls30 3.6.13-2ubuntu1.3
 libgomp1 10.2.0-5ubuntu1~20.04
 libgpg-error0 1.37-1
 libgpm2 1.20.7-5
 libgssapi3-heimdal 7.7.0+dfsg-1ubuntu1
 libhcrypto4-heimdal 7.7.0+dfsg-1ubuntu1
 libheimbase1-heimdal 7.7.0+dfsg-1ubuntu1
 libheimntlm0-heimdal 7.7.0+dfsg-1ubuntu1
 libhogweed5 3.5.1+really3.5.1-2
 libhx509-5-heimdal 7.7.0+dfsg-1ubuntu1
 libidn2-0 2.2.0-2
 libisl22 0.22.1-1
 libitm1 10.2.0-5ubuntu1~20.04
 libkmod2 27-1ubuntu2
 libkrb5-26-heimdal 7.7.0+dfsg-1ubuntu1
 libksba8 1.3.5-2
 libldap-2.4-2 2.4.49+dfsg-2ubuntu1.5
 libldap-common 2.4.49+dfsg-2ubuntu1.5
 liblocale-gettext-perl 1.07-4
 liblsan0 10.2.0-5ubuntu1~20.04
 liblz4-1 1.9.2-2
 liblzma5 5.2.4-1ubuntu1
 libmpc3 1.1.0-1
 libmpfr6 4.0.2-1
 libncursesw6 6.2-0ubuntu2
 libnettle7 3.5.1+really3.5.1-2
 libnpth0 1.6-1
 libp11-kit0 0.23.20-1ubuntu0.1
 libpam-modules 1.3.1-5ubuntu4.1
 libpam-modules-bin 1.3.1-5ubuntu4.1
 libpam0g 1.3.1-5ubuntu4.1
 libpcre2-8-0 10.34-7
 libperl5.30 5.30.0-9ubuntu0.2
 libquadmath0 10.2.0-5ubuntu1~20.04
 libreadline8 8.0-4
 libroken18-heimdal 7.7.0+dfsg-1ubuntu1
 libsasl2-2 2.1.27+dfsg-2
 libsasl2-modules 2.1.27+dfsg-2
 libsasl2-modules-db 2.1.27+dfsg-2
 libseccomp2 2.4.3-1ubuntu3.20.04.3
 libselinux1 3.0-1build2
 libsemanage-common 3.0-1build2
 libsemanage1 3.0-1build2
 libsepol1 3.0-1
 libsqlite3-0 3.31.1-4ubuntu0.2
 libssl1.1 1.1.1f-1ubuntu2.1
 libstdc++-9-dev 9.3.0-17ubuntu1~20.04
 libstdc++6 10.2.0-5ubuntu1~20.04
 libsystemd0 245.4-4ubuntu3.3
 libtasn1-6 4.16.0-2
 libtext-charwidth-perl 0.04-10
 libtext-iconv-perl 1.7-7
 libtext-wrapi18n-perl 0.06-9
 libtinfo6 6.2-0ubuntu2
 libtsan0 10.2.0-5ubuntu1~20.04
 libubsan1 10.2.0-5ubuntu1~20.04
 libudev1 245.4-4ubuntu3.3
 libunistring2 0.9.10-2
 libwind0-heimdal 7.7.0+dfsg-1ubuntu1
 libzstd1 1.4.4+dfsg-3
 linux-libc-dev 5.4.0-59.65
 lsb-base 11.1.0ubuntu2
 lsb-release 11.1.0ubuntu2
 make 4.2.1-1.2
 manpages 5.05-1
 manpages-dev 5.05-1
 netbase 6.1
 openssl 1.1.1f-1ubuntu2.1
 passwd 1:4.8.1-1ubuntu5.20.04
 patch 2.7.6-6
 perl 5.30.0-9ubuntu0.2
 perl-base 5.30.0-9ubuntu0.2
 perl-modules-5.30 5.30.0-9ubuntu0.2
 pinentry-curses 1.1.0-3build1
 readline-common 8.0-4
 sudo 1.8.31-1ubuntu1.1
 tar 1.30+dfsg-7
 ubuntu-keyring 2020.02.11.2
 xz-utils 5.2.4-1ubuntu1
 zlib1g 1:1.2.11.dfsg-2ubuntu1.2
DistroRelease: Ubuntu 20.04
InstallationDate: Installed on 2020-12-12 (25 days ago)
InstallationMedia: Ubuntu 20.04.1 LTS "Focal Fossa" - Release amd64 (20200731)
NonfreeKernelModules: wl
PackageArchitecture: amd64
ProcCpuinfoMinimal:
 processor	: 3
 vendor_id	: GenuineIntel
 cpu family	: 6
 model		: 60
 model name	: Intel(R) Core(TM) i5-4590 CPU @ 3.30GHz
 stepping	: 3
 microcode	: 0x28
 cpu MHz		: 2531.888
 cache size	: 6144 KB
 physical id	: 0
 siblings	: 4
 core id		: 3
 cpu cores	: 4
 apicid		: 6
 initial apicid	: 6
 fpu		: yes
 fpu_exception	: yes
 cpuid level	: 13
 wp		: yes
 flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts md_clear flush_l1d
 bugs		: cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit srbds
 bogomips	: 6584.89
 clflush size	: 64
 cache_alignment	: 64
 address sizes	: 39 bits physical, 48 bits virtual
 power management:
ProcVersionSignature: Ubuntu 5.4.0-58.64-generic 5.4.73
Python3Details: /usr/bin/python3.8, Python 3.8.5, python3-minimal, 3.8.2-0ubuntu2
PythonDetails: N/A
RelatedPackageVersions:
 dpkg 1.19.7ubuntu3
 apt  2.0.2ubuntu0.2
Tags:  focal
Uname: Linux 5.4.0-58-generic x86_64
UpgradeStatus: No upgrade log present (probably fresh install)
_MarkForUpload: True
```

---

### Post by paul_wilson2 on 2021-01-08
Found an alternative solution while tracing errors in bcmwl-kernel-source.

 see [https://unix.stackexchange.com/questions/416180/ubuntu-no-wifi-adapter-found](https://unix.stackexchange.com/questions/416180/ubuntu-no-wifi-adapter-found)

I tried the solution listed in the thread, which involves purging the  bcmwl-kernel-source and installed broadcom-sta and it work for me in  Ubuntu 20.04 LTS with the Linux 5.8.0-36 headers installed.

sudo apt-get purge bcmwl-kernel-source

sudo apt-get install broadcom-sta-source broadcom-sta-dkms broadcom-sta-common

---

### Post by #&amp;thj^% on 2021-01-08
It did not happen to me so I'm winging it from here, but this should work.

Purge all packages related to kernel 5.8.0-34-generic: 
```
sudo apt purge linux-image-5.8.0-34-generic linux-image-unsigned-5.8.0-34-generic linux-modules-5.8.0-34-generic linux-headers-5.8.0-34-generic
```
[list]
    [*]Purge the Broadcom WiFi driver: 
```
sudo apt purge bcmwl-kernel-source
```
    [*]Remove redundant packages: 
```
sudo apt autoremove
```
    Put the 5.4.0-59-generic kernel on hold:
```
sudo apt-mark hold 5.4.0-59-generic
```
    [*]Update package metadata: 
```
sudo apt update
```
    [*]Re-install the driver: 
```
sudo apt install bcmwl-kernel-source
```[/list]

Since the 5.8.0-34-generic kernel is gone, the driver is compiled only for the 5.4.0-59-generic kernel which succeeds as expected. Reboot, and WiFi should be restored.
**EDIT:** Ya know I've yet to see this on 20.10>>>Huum makes me wonder???
> 2020-10-02 - Alberto Milone <alberto.milone@canonical.com>
bcmwl (6.30.223.271+bdcom-0ubuntu7) groovy; urgency=medium
* debian/patches/0028-add-support-for-linux-5.6.patch:
- Remove extra src prefix, which prevented the patch from
being applied correctly (LP: #1878045).
If this still dose not succeed ley me know, I think "bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu7_amd64.deb" from 20.10 might work as a last resort, **BUT PLEASE DON"T try this just yet OK?**
Kind of fun seeing this at AU also:[https://askubuntu.com/questions/1305699/bcmwl-kernel-source-broken-on-kernel-5-8-0-34-generic](https://askubuntu.com/questions/1305699/bcmwl-kernel-source-broken-on-kernel-5-8-0-34-generic)

---

### Post by eZtaR on 2021-01-08
Thanks a bunch 1fallen, it worked! :D

---

### Post by #&amp;thj^% on 2021-01-08
Great!! Happy buntu-ing :)
**Wait I nearly forgot to un-hold your kernel for updates. **
```

sudo apt-mark unhold 5.4.0-59-generic
```
Post back here: if any other problems arise on the "WiFi" front.

---

### Post by sangresani on 2021-01-09
Hey,
I had the same problem and I need some additional info if that's possible. 
I did "apt upgrade" and it upgraded the kernel to 5.8.0-36. The Wi-Fi went to hell, so I did what 1fallen wrote and it works (BIG THANKS).

Now I need some clarification on the kernel thing (I'm newb in kernel stuff :(). If I understand correctly, I'm now back on 5.4.0-59 kernel. But when I do "apt upgrade" now, this time it doesn't try to upgrade the kernel to 5.8.0-xx.  Why?

---

### Post by #&amp;thj^% on 2021-01-09
> **sangresani said:**
> 
Now I need some clarification on the kernel thing (I'm newb in kernel stuff :(). If I understand correctly, I'm now back on 5.4.0-59 kernel. But when I do "apt upgrade" now, this time it doesn't try to upgrade the kernel to 5.8.0-xx.  Why?

 It's an LTS release kernel should of had a higher priority, meaning installing kernel 5.8 should of only happened if the user installed it.
Not official yet but 5.10 of the kernel series will be the next LTS

---

