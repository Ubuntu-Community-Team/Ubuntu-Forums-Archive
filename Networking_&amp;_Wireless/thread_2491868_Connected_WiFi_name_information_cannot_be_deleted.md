---
title: "Connected WiFi name information cannot be deleted"
date: 2023-10-23
forum: Networking &amp; Wireless
---

### Post by virtual163 on 2023-10-23
Hi, guys,






The following issue occurred in Ubuntu 23.10. When I tried to delete the WIFI information that had already been memorized, I found that the deleted information was indeed missing. However, after the system restarted, the deleted WIFI information returned






I also tried to stop Tptables, but it still didn't work.






I am not sure what caused this issue, and now I am unable to delete the saved network information.






Here are some things I have tried:






1) Nmcli c






Status:


$nmcli c


NAME UUID TYPE DIVICE


WEB WIFI eff2f46d-6167-4de2-ac92-5d711b5b821b wifi wlp9s0


Lo cb8d2101-6af5-458c-929d-1522bb6a2375 loopback lo


China Unicom f914356b-d224-4c01-a67d-d60fb089295d gsm cdc-wdm0


21712 bc03f382-9636-470d-af9f-5bd8cf8ef17d wifi--


AWiFi WHBG-8902 9de7eb79-30cd-4776-8b7f-f62767fb14df wifi--


BDIA_ FREE_ WIFI 89801902-a89a-42e4-8a6f-9be80b160455 wifi--


ChinaNet-4005 36228581-efa7-4499-9d40-4c8bec3d0161 wifi--


ChinaNet-821 f50e33c5-d45d-438a-bb57-198f7a0b15c0 wifi--


ChinaNet DCRxUK 589d8691-b9f6-4958-88a5-0ad56b32e896 wifi--


CMCC-XN2H eacb6958-5fc4-42ff-a817-b77b3b44e9a1 wifi--






2) Nmcli c delete ChinaNet-821


Nmcli c delete ChinaNet-DCRxUK






Status:


L - $nmcli c delete ChinaNet-821


Connection 'ChinaNet-821' (f50e33c5-d45d-438a-bb57-198f7a0b15c0) successfully deleted


&#322; -[ mrchen@MrChen-T14 ]- [~]


L - $nmcli c delete ChinaNet DCRxUK


Connection 'ChinaNet DCRxUK' (589d8691-b9f6-4958-88a5-0ad56b32e896) successfully deleted


&#322; -[ mrchen@MrChen-T14 ]- [~]






3) Nmcli c






Status:


$nmcli c


NAME UUID TYPE DIVICE


WEB WIFI eff2f46d-6167-4de2-ac92-5d711b5b821b wifi wlp9s0


Lo cb8d2101-6af5-458c-929d-1522bb6a2375 loopback lo


China Unicom f914356b-d224-4c01-a67d-d60fb089295d gsm cdc-wdm0


21712 bc03f382-9636-470d-af9f-5bd8cf8ef17d wifi--


AWiFi WHBG-8902 9de7eb79-30cd-4776-8b7f-f62767fb14df wifi--


BDIA_ FREE_ WIFI 89801902-a89a-42e4-8a6f-9be80b160455 wifi--


ChinaNet-4005 36228581-efa7-4499-9d40-4c8bec3d0161 wifi--


CMCC-XN2H eacb6958-5fc4-42ff-a817-b77b3b44e9a1 wifi--






4) Reboot






5) $nmcli c






$nmcli c


NAME UUID TYPE DIVICE


WEB WIFI eff2f46d-6167-4de2-ac92-5d711b5b821b wifi wlp9s0


Lo cb8d2101-6af5-458c-929d-1522bb6a2375 loopback lo


China Unicom f914356b-d224-4c01-a67d-d60fb089295d gsm cdc-wdm0


21712 bc03f382-9636-470d-af9f-5bd8cf8ef17d wifi--


AWiFi WHBG-8902 9de7eb79-30cd-4776-8b7f-f62767fb14df wifi--


BDIA_ FREE_ WIFI 89801902-a89a-42e4-8a6f-9be80b160455 wifi--


ChinaNet-4005 36228581-efa7-4499-9d40-4c8bec3d0161 wifi--


ChinaNet-821 f50e33c5-d45d-438a-bb57-198f7a0b15c0 wifi--


ChinaNet DCRxUK 589d8691-b9f6-4958-88a5-0ad56b32e896 wifi--


CMCC-XN2H eacb6958-5fc4-42ff-a817-b77b3b44e9a1 wifi--






Even after restarting many times, I cannot delete the memorized WIFI information






Thank you very much for your help






thanks

---

### Post by chili555 on 2023-10-24
May we please see:

```
uname -r
ls /etc/netplan/
sudo ls /etc/NetworkManager/system-connections/

```

Thanks.

---

### Post by virtual163 on 2023-10-25
Not for this reason, it's an error message
> [COLOR=#695028][FONT=Monaco]2023[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]-10[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]-24[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]T17:[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]14[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]:[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]03.741639[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]+[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]08[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]:[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]00[/FONT][/COLOR][COLOR=#695028][FONT=Monaco] MrChen-Duet NetworkManager[[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]700[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]]: netplan_delete_connection: Cannot write output state: Read-only file system[/FONT][/COLOR]
[COLOR=#695028][FONT=Monaco]2023[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]-10[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]-24[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]T17:[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]14[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]:[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]03.811173[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]+[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]08[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]:[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]00[/FONT][/COLOR][COLOR=#695028][FONT=Monaco] MrChen-Duet generate[[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]1795[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]]: Permissions [/FONT][/COLOR][COLOR=#A71D5D][FONT=Monaco]for[/FONT][/COLOR][COLOR=#695028][FONT=Monaco] /etc/netplan/[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]01[/FONT][/COLOR][COLOR=#695028][FONT=Monaco]-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible [/FONT][/COLOR][COLOR=#A71D5D][FONT=Monaco]by[/FONT][/COLOR][COLOR=#695028][FONT=Monaco] others.[/FONT][/COLOR]

---

### Post by chili555 on 2023-10-25
> Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.

Please do: ```
sudo chmod 0600 /etc/netplan/01-network-manager-all.yaml

```
And try again. Run and post:

```
uname -r
ls /etc/netplan/
sudo ls /etc/NetworkManager/system-connections/

```

---

### Post by virtual163 on 2023-10-26
The permissions have been changed, still the same as before
> drwxr-xr-x   2 root root  4096 Oct 26 12:35 ./drwxr-xr-x 156 root root 12288 Oct 26 06:54 ../
-rw-r--r--   1 root root    49 Oct 26 12:41 01-network-manager-all.yaml
-rw-------   1 root root   350 Oct 26 12:33 50-cloud-init.yaml


---

### Post by chili555 on 2023-10-26
Please try again. Here is a sequence from my machine:

```
chili@T480s:~$ ls -al /etc/netplan
total 28
drwxr-xr-x   2 root root  4096 Oct 24 21:15 .
drwxr-xr-x 144 root root 12288 Oct 26 09:02 ..
-rw-------   1 root root   686 Oct 24 21:08 90-NM-7f6a828b-ff8b-4840-b778-571ce299feed.yaml
-rw-------   1 root root   686 Oct 24 21:09 90-NM-d85106a2-ecf8-4493-8ec5-d93431386ece.yaml
[COLOR="#FF0000"]-rwxrwxrwx [/COLOR]  1 root root    49 Oct 24 21:02 network_manager.yaml **<---wrong permissions**
chili@T480s:~$ sudo chmod 0600 /etc/netplan/network_manager.yaml **<---change permissions**
chili@T480s:~$ ls -al /etc/netplan
total 28
drwxr-xr-x   2 root root  4096 Oct 24 21:15 .
drwxr-xr-x 144 root root 12288 Oct 26 09:02 ..
-rw-------   1 root root   686 Oct 24 21:08 90-NM-7f6a828b-ff8b-4840-b778-571ce299feed.yaml
-rw-------   1 root root   686 Oct 24 21:09 90-NM-d85106a2-ecf8-4493-8ec5-d93431386ece.yaml
[COLOR="#FF0000"]-rw------- [/COLOR]  1 root root    49 Oct 24 21:02 network_manager.yaml **<---correct permissions**

```

---

