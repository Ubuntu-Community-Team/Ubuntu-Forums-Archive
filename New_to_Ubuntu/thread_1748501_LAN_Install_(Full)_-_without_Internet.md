---
title: "LAN Install (Full) - without Internet"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by bhavani.lug on 2011-05-03
Greetings, Fellow Ubuntu users.

I have a question on the Ubuntu netboot:

Setup:
1. I have a Windows server - serving as DHCP, PXE server & Webserver (Hosting the contents of a Ubuntu 10.04 LTS Server CD)

2. I have a Ubuntu Webserver hosting the contents of Apt-Mirror mirrored from archive.ubuntu.com for Lucid

3. Target machine is a intel based PC

Process - I (Pxe pointing 10.04LTS CD contents):
1. I start the target machine and hit F12 for a Pxe boot.
2. After the network address is assigned by DHCP, the installer wants to look at *internet* to download files for the install.
3. It reads the preseed file for a fully automated install (no questions asked)
4. I point the mirror location to the 10.04LTS cd contents hosted on the local webserver.
5. The installer says that it is not able to find many deb files in that location

Process - II (Pxe pointing to a local mirror <mirrored from archive.ubuntu.com>)
1. I start the target machine and hit F12 for a Pxe boot.
2. After the network address is assigned by DHCP, the installer complains that the packages.gz file does not match the md5sum on the Release file. (And, they were mirrored from an ubuntu official archive)
3. It reads the preseed file for a fully automated install (no questions asked)
4. I change the checksums on the Release file to match the originals.
5. Debian installer still cannot find many deb files

Requirement:
1. Target machine to complete the install locally using Pxe without seeking Internet mirrors for any file.
2. Prefer to use the complete source to be available through HTTP
3. Unattended install using a preseed file hosted on the webserver

Any help to this requirement will be greatly appreciated. 
Thank you.

-Bhavani

---

