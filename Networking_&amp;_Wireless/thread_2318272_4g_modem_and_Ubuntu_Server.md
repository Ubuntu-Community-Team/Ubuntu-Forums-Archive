---
title: "4g modem and Ubuntu Server"
date: 2016-03-24
forum: Networking &amp; Wireless
---

### Post by wagner3 on 2016-03-24
Hello guys. 

I'm trying to setup a 4g modem (Huawei E8372) on a pc runing Ubuntu Server 12.04. My goal is to make zabbix send sms alert messages to my cell phone.

I'm very green at all this, but what I did this far was:

I plugged the modem on a usb port, lsusb show this:

[TABLE="width: 100%"]
[TR="class: ui_form_pair"]
[TD="class: ui_form_value, colspan: 2"][B]> lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 12d1:14db Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 04f2:0116 Chicony Electronics Co., Ltd KU-2971/KU-0325 Keyboard
Bus 002 Device 004: ID 04f2:0939 Chicony Electronics Co., Ltd 

[/B][SIZE=2][FONT=Verdana]Ok, then I did some research and find out I should change the /lib/udev/rules.d/40-usb_modeswitch.rules file, so I included the following lines:

[/FONT][/SIZE][SIZE=4][COLOR=#000000]# Huawei E8372 (Vivo)
ATTR{idVendor}=="12d1", ATTR{idProduct}=="14db", RUN+="usb_modeswitch '%b/%k'"

[/COLOR][SIZE=3]I still can't  get sms messages. I don't know if this a problem with Zabbix or the modem setup.

[/SIZE][/SIZE]So, is there a way to send a test SMS message so I can know if the devide is working properly? I'm really lost here guys, any help will be really appreciated.

Thank you.

[/TD]
[/TR]
[/TABLE]

---

