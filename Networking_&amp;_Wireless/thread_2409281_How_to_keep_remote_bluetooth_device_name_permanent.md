---
title: "How to keep remote bluetooth device name permanently?"
date: 2018-12-30
forum: Networking &amp; Wireless
---

### Post by Mailosealsul on 2018-12-30
Hello all
I am setting MAME(Multiple Arcade Machine Emulator) in Ubuntu 18.04

Everthing is OK but I am stuck with Joystick configuration at the moment.

MAME only detects Joystick by it's "name" , not device path like /dev/input/***.
Then, I open to modify my bluetooth joystick name in > /var/lib/bluetooth/[parent MAC Address]/[remote bluetooth Joystick MAC address]/info
Result is following
> [General]
  Name=8Bitdo SF30 Pro
  Class=0x002508
  SupportedTechnologies=BR/EDR;
  Trusted=true
  Blocked=false
  Services=00001124-0000-1000-8000-00805f9b34fb;00001200-0000-1000-8000-00805f9b34fb;
  Alias=Joypad2
  
  [LinkKey]
  Key=582BE4432D3EB24A4901454D70F51C82
  Type=4
  PINLength=0
 
  [DeviceID]
  Source=2
  Vendor=1118
  Product=736
  Version=2307

And modified name in Line 2 from
> NAME = 8Bitdo SFC30 PRO to > NAME = 8Bitdo SFC30 PRO P1 since it should be player1 joystick.
I need to keep this name since I have same 4 joysticks.(others name should be 8Biddo SFC30 PRO P2 , P3, P4..)

After modification, I ran > sudo service bluetooth restart and would be everyting fine.
Bluetooth Panel in desktop showed they are modified well.

but, Once I turned on joysticks for paring, then Joystick name changed back to original name "8Bidto SFC30 PRO".
I repeated this several times and this is happening randomly.(sometimes keep the name designated, but sometimes changed back to original name)

Finally, I did some trick that modified permission of "/var/lib/bluetooth/[system MAC Address]/[remote bluetooth Joystick MAC address]/info" from 600 to 400(for even root can read only)
but, this trick didn't work...
Interestingly, once bluetooth name changed back, "/var/lib/bluetooth/xxxx/xxx/info" stayed with changed the name(of course , only read permission)
, but Bluetooth Panel showed original name.

Some post advised to use Blueman to change the name but it only support for Alias on the device, not changing device name

I think there maybe some other solution to control remote bluetooth name.
I already googled a lot but still no success.

Anyone can help on this?

---

