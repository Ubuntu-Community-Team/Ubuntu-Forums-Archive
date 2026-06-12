---
title: "issues in configuring Huawei E1550 in ubunto 10.10"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by ajeesh cherian on 2010-10-24
Hi,

I am having issues in mounting Huawei E1550 in ubunto 10.10; thing is that after  plugging in the usb modem the windows partitions mounted are also gone.

I have checked /etc/udev/rules.d
Under 70-persistent-cd.rules I could see a rule to 'block' the device  mounting is added automatically after Huawai E1550 is plugged in. Below  is the entry

# Mass_Storage (pci-0000:00:12.2-usb-0:3:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HUAWEI_Mass_Storage-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"

It also says

# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


I have tried adding another rule, but no go.
[http://blog.lynxworks.eu/2009/08/hua...550-on-ubuntu/]("http://blog.lynxworks.eu/2009/08/huawei-e1550-on-ubuntu/") (refered by **gandaran**)

Does the above scenario  rings any bell to anyone? Please help me in configuring my 3G  modem....!!
I had posted this query earlier, please check my post at [post10007827]("http://ubuntuforums.org/showthread.php?p=10007827&posted=1#post10007827")

I have
1. Updated ubuntu 10.10 - 70 packages
2. Tried reinstalling modeswitch, tried previous version of modeswitch (but not getting installed)
3. Uninstalled modestwitch completely, but device is not mounting as mass storage.


Plz...plz...anybody help me...:(

---

### Post by C.S.Cameron on 2010-10-24
I use a Huawei 3G modem when I am home in Sri Lanka.
I just plug it in, go to Network Connections / Mobile Broadband / Add / Select Providers Country / and then select my provider from the drop down list.

I will be trying it with 10.10 next week.

---

### Post by ajeesh cherian on 2010-10-27
Alright...plz check...till now I cannot find a way to resolve this issue.
In 10.04 LTS after installing modeswitch I can connect using the steps you have given....but not in 10.10!!

please check my detail post regarding this issue at [post10007827]("http://ubuntuforums.org/showthread.php?p=10007827&posted=1#post10007827")

Thank you
Ajeesh Cherian

---

### Post by Elfy on 2010-10-27
Closed - please do not post duplicate threads.

---

