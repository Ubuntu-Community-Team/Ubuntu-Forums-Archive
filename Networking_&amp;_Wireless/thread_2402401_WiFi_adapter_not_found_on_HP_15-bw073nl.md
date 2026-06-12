---
title: "WiFi adapter not found on HP 15-bw073nl"
date: 2018-09-29
forum: Networking &amp; Wireless
---

### Post by lucabussi94 on 2018-09-29
HI everyone, I have just installed on my HP 15-bw073nl laptop Ubuntu 18.04 and everything seems work correctly except for the WiFi.
If i look to the tool it says "WiFi adapter not found"
I tried some solutions I found online but nothing seems work, nothing changes.
Can someone help a new linux user without expertise? (I'm not new to coding or technological stuffs but I'm new in linux) 
Thanks
Luca

---

### Post by jeremy31 on 2018-09-29
Post results for ```
lspci -nnk | grep -iA3 net; mokutil --sb-status
```

---

### Post by lucabussi94 on 2018-09-29
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8330]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]
    Kernel modules: rtl8723de, wl
mokutil: unrecognized option '--sb-status'
Usage:
  mokutil OPTIONS [ARGS...]

Options:
  --help                Show help
  --list-enrolled            List the enrolled keys
  --list-new                List the keys to be enrolled
  --list-delete                List the keys to be deleted
  --import <der file...>        Import keys
  --delete <der file...>        Delete specific keys
  --revoke-import            Revoke the import request
  --revoke-delete            Revoke the delete request
  --export                Export enrolled keys to files
  --password                Set MOK password
  --clear-password            Clear MOK password
  --disable-validation            Disable signature validation
  --enable-validation            Enable signature validation
  --sb-state                Show SecureBoot State
  --test-key <der file>            Test if the key is enrolled or not
  --reset                Reset MOK list
  --generate-hash[=password]        Generate the password hash
  --ignore-db                Ignore DB for validation
  --use-db                Use DB for validation
  --import-hash <hash>            Import a hash into MOK or MOKX
  --delete-hash <hash>            Delete a hash in MOK or MOKX
  --set-verbosity <true/false>        Set the verbosity bit for shim
  --pk                    List the keys in PK
  --kek                    List the keys in KEK
  --db                    List the keys in db
  --dbx                    List the keys in dbx

Supplimentary Options:
  --hash-file <hash file>        Use the specific password hash
  --root-pw                Use the root password
  --simple-hash                Use the old password hash method
  --mokx                Manipulate the MOK blacklist


```

---

### Post by jeremy31 on 2018-09-29
```
mokutil --sb-state
```
I am guessing that Secure Boot is enabled
And do a ```
sudo apt remove bcmwl-kernel-source
```
Reboot and go into BIOS/UEFI and disable Secure Boot

---

### Post by lucabussi94 on 2018-09-29
WiFi now is working! thank's a lot!

But the signal of the networks compared with windows is very low, can i do something?

---

### Post by jeremy31 on 2018-09-29
Yes,  for current boot ```
sudo modprobe -r rtl8723de && sudo modprobe rtl8723de ant_sel=2
```

For semi permanent solution ```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
That will make the first terminal command work after rebooting

---

### Post by lucabussi94 on 2018-09-30
it works perfectly and, after those thinks it seems that also the Bluetooth problems  are fixed, thank you very much.

I have just one thinks remain and you seems to know a lot about ubuntu so I try to ask you: The volume is lower than windows volume, do you know a solution also for that? O:)

---

