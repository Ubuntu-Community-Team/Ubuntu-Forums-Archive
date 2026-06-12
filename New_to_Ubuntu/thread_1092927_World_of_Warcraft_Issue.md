---
title: "World of Warcraft Issue"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Dreygz on 2009-03-10
So i installed it and did what i think is everything the guide says to do but every time i start the game i can't even get to the login screen and this error pops up. Help plz.

==============================================================================

World of WarCraft (build 9551)



Exe:      C:\Program Files\World of Warcraft\Wow.exe

Time:     Mar 10, 2009  8:26:42.355 PM

User:     taylor

Computer: taylor-desktop

------------------------------------------------------------------------------



This application has encountered a critical error:



ERROR #132 (0x85100084) Fatal Exception

Program:	C:\Program Files\World of Warcraft\Wow.exe

Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000000



The instruction at "0x00000000" referenced memory at "0x00000000".

The memory could not be "read".





WoWBuild: 9551

Settings: 

SET readTOS "-1"

SET readEULA "-1"

SET readScanning "-1"

SET readContest "-1"

SET readTerminationWithoutNotice "-1"

SET installType "Retail"

SET checkAddonVersion "1"

SET locale "enUS"

SET expansionMovie "1"

SET movie "1"

SET showToolsUI "1"

SET portal "us"

SET realmList "us.logon.worldofwarcraft.com"

SET patchlist "us.version.worldofwarcraft.com"

SET coresDetected "2"

------------------------------------------------------------------------------



----------------------------------------

    x86 Registers

----------------------------------------



EAX=00000000  EBX=7E030C90  ECX=00000000  EDX=00000000  ESI=00000000

EDI=7E00FFAD  EBP=003AF0AC  ESP=003AEAE0  EIP=00000000  FLG=00210246

CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B





----------------------------------------

    Stack Trace (Manual)

----------------------------------------



Address  Frame    Logical addr  Module



Showing 1/1 threads...



--- Thread ID: 88 [Current Thread] ---

00000000 003AF0AC 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe

7DFFED12 003AF0DC 0001:000CDD12 C:\windows\system32\wined3d.dll

7E048420 003AF10C 0001:00007420 C:\windows\system32\d3d9.dll

005DE85A 003AF120 0001:001DD85A C:\Program Files\World of Warcraft\Wow.exe

005D96C7 003AF738 0001:001D86C7 C:\Program Files\World of Warcraft\Wow.exe

006A3492 003AFB64 0001:002A2492 C:\Program Files\World of Warcraft\Wow.exe

0069F3D0 003AFC10 0001:0029E3D0 C:\Program Files\World of Warcraft\Wow.exe

004066F0 003AFE5C 0001:000056F0 C:\Program Files\World of Warcraft\Wow.exe

004068D7 003AFE6C 0001:000058D7 C:\Program Files\World of Warcraft\Wow.exe

00406958 003AFF08 0001:00005958 C:\Program Files\World of Warcraft\Wow.exe

7B8776A9 003AFFE8 0001:000566A9 C:\windows\system32\KERNEL32.dll



----------------------------------------

    Stack Trace (Using DBGHELP.DLL)

----------------------------------------



Showing 1/1 threads...



--- Thread ID: 88 [Current Thread] ---

7DFFED12 wined3d.dll  WineDirect3DCreate+34 (0x00000009,0x0013D2F0,0x00000010,0x7B86778D)

7E048420 d3d9.dll     Direct3DCreate9+112 (0x00000020,0x00000000,0x00000000,0x003AF738)

005DE85A Wow.exe      <unknown symbol>+0 (0x003AF730,0x003AF734,0x011F2638,0x011F263A)

005D96C7 Wow.exe      <unknown symbol>+0 (0x011F2638,0x011F263A,0x011F263C,0x011F2640)

006A3492 Wow.exe      <unknown symbol>+0 (0x011F2638,0x011F2949,0x00973CA0,0x00973CAC)

0069F3D0 Wow.exe      <unknown symbol>+0 (0x003AFC24,0x00000001,0x00000001,0x6C726F57)

004066F0 Wow.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x003AFF08,0x00406958)

004068D7 Wow.exe      <unknown symbol>+0 (0x0040ABB9,0x00400000,0x00000000,0x00111B54)

00406958 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)

7B8776A9 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)





----------------------------------------

    Loaded Modules

----------------------------------------



0x00400000 - 0x01391000  C:\Program Files\World of Warcraft\Wow.exe

0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll

0x7B820000 - 0x7B93C000  C:\windows\system32\KERNEL32.dll

0x7BC10000 - 0x7BCAE000  C:\windows\system32\ntdll.dll

0x7D5F0000 - 0x7D5F9000  C:\windows\system32\psapi.dll

0x7D600000 - 0x7D645000  C:\windows\system32\dbghelp.dll

0x7D680000 - 0x7D6A5000  C:\windows\system32\uxtheme.dll

0x7D6D0000 - 0x7D6E1000  C:\windows\system32\midimap.dll

0x7D6F0000 - 0x7D6F8000  C:\windows\system32\msacm32.drv

0x7D7C0000 - 0x7D7F0000  C:\windows\system32\winealsa.drv

0x7D830000 - 0x7D8BB000  C:\windows\system32\winex11.drv

0x7DA00000 - 0x7DA59000  C:\windows\system32\rpcrt4.dll

0x7DA70000 - 0x7DB65000  C:\windows\system32\ole32.dll

0x7DB70000 - 0x7DB8C000  C:\windows\system32\msacm32.dll

0x7DB90000 - 0x7DBB9000  C:\windows\system32\ws2_32.dll

0x7DBC0000 - 0x7DC7A000  C:\windows\system32\comctl32.dll

0x7DC90000 - 0x7DE06000  C:\windows\system32\shell32.dll

0x7DE10000 - 0x7DE61000  C:\windows\system32\shlwapi.dll

0x7DE70000 - 0x7DE83000  C:\windows\system32\mpr.dll

0x7DE90000 - 0x7DED4000  C:\windows\system32\wininet.dll

0x7DEE0000 - 0x7DEF4000  C:\windows\system32\imm32.dll

0x7DF00000 - 0x7DF08000  C:\windows\system32\lz32.dll

0x7DF10000 - 0x7DF21000  C:\windows\system32\version.dll

0x7DF30000 - 0x7E033000  C:\windows\system32\wined3d.dll

0x7E040000 - 0x7E065000  C:\windows\system32\d3d9.dll

0x7EB20000 - 0x7EBA0000  C:\windows\system32\opengl32.dll

0x7EBB0000 - 0x7EBF4000  C:\windows\system32\advapi32.dll

0x7EC00000 - 0x7EC92000  C:\windows\system32\gdi32.dll

0x7ECB0000 - 0x7EDDB000  C:\windows\system32\user32.dll

0x7EDF0000 - 0x7EE6D000  C:\windows\system32\winmm.dll





----------------------------------------

    Memory Dump

----------------------------------------



Code: 16 bytes starting at (EIP = 00000000)



00000000: <can't read from this address>





Stack: 1024 bytes starting at (ESP = 003AEAE0)



* = addr  **                                                  *               

003AEAE0: 1B 5B F8 7D  01 00 00 00  88 EF 3A 00  58 80 00 00  .[.}......:.X...

003AEAF0: 04 00 00 00  04 00 00 00  00 00 00 00  E1 80 00 00  ................

003AEB00: 67 83 00 00  00 00 00 00  00 00 00 00  00 00 00 00  g...............

003AEB10: 00 00 00 00  50 D3 13 00  50 01 00 00  3C EB 3A 00  ....P...P...<.:.

003AEB20: 24 DE D1 B7  2E 08 00 00  8A 11 01 7E  07 26 01 7E  $..........~.&.~

003AEB30: AD FF 00 7E  16 29 01 7E  1C F9 00 7E  9C EF 3A 00  ...~.).~...~..:.

003AEB40: 8C EF 3A 00  88 EF 3A 00  E0 A6 02 7E  58 EF 3A 00  ..:...:....~X.:.

003AEB50: 30 EF 3A 00  C0 17 03 7E  F0 EE 3A 00  F4 0F E0 B7  0.:....~..:.....

003AEB60: CC 1A 03 7E  B0 1A 03 7E  9D F0 D1 B7  20 03 00 00  ...~...~.... ...

003AEB70: E0 FE 13 00  E7 D5 CA 7B  A9 00 00 00  01 00 00 00  .......{........

003AEB80: 02 00 00 00  55 00 00 00  0A 00 00 00  E5 30 01 7E  ....U........0.~

003AEB90: 01 00 00 00  40 58 08 7C  71 9D 09 7C  C7 68 8B 7D  ....@X.|q..|.h.}

003AEBA0: C2 23 E3 B7  AC 11 F5 B7  48 03 00 00  5C 00 5C 00  .#......H...\.\.

003AEBB0: 2E 00 5C 00  44 00 49 00  53 00 50 00  4C 00 41 00  ..\.D.I.S.P.L.A.

003AEBC0: 59 00 31 00  00 00 11 00  0C D6 CA 7B  EC EB 3A 00  Y.1........{..:.

003AEBD0: 14 27 C6 7B  00 8C FD 7F  B8 0D 11 00  00 8C FD 7F  .'.{............

003AEBE0: 28 25 C9 7B  00 80 FD 7F  98 EC 3A 00  58 00 31 00  (%.{......:.X.1.

003AEBF0: 31 00 20 00  57 00 69 00  6E 00 64 00  6F 00 77 00  1. .W.i.n.d.o.w.

003AEC00: 69 00 6E 00  67 00 20 00  53 00 79 00  73 00 74 00  i.n.g. .S.y.s.t.

003AEC10: 65 00 6D 00  00 00 3A 00  00 8C FD 7F  F0 D2 13 00  e.m...:.........

003AEC20: 00 00 00 00  2F 01 00 00  3C EC 3A 00  00 00 00 00  ..../...<.:.....

003AEC30: 54 F2 3A 00  E3 BC D7 B7  28 25 C9 7B  CC F2 3A 00  T.:.....(%.{..:.

003AEC40: 40 09 E0 B7  00 00 00 00  68 D3 13 00  28 25 C9 7B  @.......h...(%.{

003AEC50: BC ED 3A 00  00 00 00 00  28 ED 3A 00  28 25 C9 7B  ..:.....(.:.(%.{

003AEC60: 00 04 00 00  44 21 D7 7E  A8 EC 3A 00  96 58 C3 7B  ....D!.~..:..X.{

003AEC70: E8 D1 CA 7B  00 04 00 00  AD 55 C8 7B  E4 EC 3A 00  ...{.....U.{..:.

003AEC80: 28 25 C9 7B  BC ED 3A 00  D8 EC 3A 00  44 00 00 00  (%.{..:...:.D...

003AEC90: E8 D1 CA 7B  F3 28 E1 B7  B1 F6 3A 00  00 00 00 00  ...{.(....:.....

003AECA0: E8 D1 CA 7B  2C D2 CA 7B  00 00 00 00  30 8E C4 7B  ...{,..{....0..{

003AECB0: 28 25 C9 7B  00 80 FD 7F  2C EE 3A 00  0C EE 3A 00  (%.{....,.:...:.

003AECC0: 49 9C C4 7B  9C ED 3A 00  2C EE 3A 00  98 ED 3A 00  I..{..:.,.:...:.

003AECD0: 1E 00 00 00  44 21 D7 7E  08 ED 3A 00  80 5B C3 7B  ....D!.~..:..[.{

003AECE0: 44 21 D7 7E  60 ED 3A 00  C1 0C DA 7E  15 00 00 00  D!.~`.:....~....

003AECF0: 00 00 00 00  00 80 FD 7F  00 80 FD 7F  44 ED 3A 00  ............D.:.

003AED00: 9C ED 3A 00  98 ED 3A 00  48 ED 3A 00  7C F0 E2 B7  ..:...:.H.:.|...

003AED10: 2C EE 3A 00  00 00 00 00  00 8C FD 7F  F0 D2 13 00  ,.:.............

003AED20: 2F 4C C4 7B  AC 11 F5 B7  48 ED 3A 00  E0 2B 0E 00  /L.{....H.:..+..

003AED30: 14 00 11 00  30 D4 13 00  00 00 14 00  00 00 11 00  ....0...........

003AED40: C2 23 E3 B7  AC 11 F5 B7  68 00 00 00  6C ED 3A 00  .#......h...l.:.

003AED50: D4 2A E3 B7  48 00 00 00  00 00 03 00  30 D4 13 00  .*..H.......0...

003AED60: 28 25 C9 7B  F0 09 23 00  AA 09 23 00  18 2D 0E 00  (%.{..#...#..-..

003AED70: 14 00 11 00  F8 D2 13 00  20 D4 13 00  00 00 11 00  ........ .......

003AED80: 28 25 C9 7B  E8 D2 13 00  38 01 00 00  DC ED 3A 00  (%.{....8.....:.

003AED90: 16 43 C4 7B  80 AE C9 7B  00 00 00 00  40 00 00 00  .C.{...{....@...

003AEDA0: 35 26 C4 7B  9C D3 13 00  FA 09 23 00  80 00 00 00  5&.{......#.....

003AEDB0: CE 31 C4 7B  00 00 00 00  FC D2 13 00  14 00 11 00  .1.{............

003AEDC0: 41 4C C3 7B  36 D3 13 00  F0 D2 13 00  14 00 11 00  AL.{6...........

003AEDD0: EF 45 C3 7B  14 00 11 00  28 25 C9 7B  1C EE 3A 00  .E.{....(%.{..:.

003AEDE0: 6F 46 C4 7B  54 00 11 00  00 00 00 00  00 00 00 00  oF.{T...........

003AEDF0: 00 00 C3 7B  20 EE 3A 00  00 00 0A FF  DD 86 C4 7B  ...{ .:........{

003AEE00: EF 45 C3 7B  00 00 00 00  00 00 11 00  02 00 00 00  .E.{............

003AEE10: 38 49 8B 7B  00 00 00 00  BC F0 3A 00  3C EE 3A 00  8I.{......:.<.:.

003AEE20: 4F 09 85 7B  00 00 11 00  00 00 00 00  F0 D2 13 00  O..{............

003AEE30: 38 49 8B 7B  00 00 00 00  BC F0 3A 00  9C F0 3A 00  8I.{......:...:.

003AEE40: A3 73 86 7B  00 00 11 00  00 00 00 00  F0 D2 13 00  .s.{............

003AEE50: 8C F0 3A 00  00 00 00 00  00 00 00 00  11 BB D6 7E  ..:............~

003AEE60: 00 00 00 00  00 00 00 00  8C F0 3A 00  D4 FF FF FF  ..........:.....

003AEE70: F0 D2 13 00  D4 FF FF FF  D4 FF FF FF  FF 5F CF B7  ............._..

003AEE80: B4 EE 3A 00  00 00 00 00  FF 5F CF B7  00 00 00 00  ..:......_......

003AEE90: D8 F3 3A 00  08 02 63 00  3A 00 3A 00  E4 F3 3A 00  ..:...c.:.:...:.

003AEEA0: 46 00 00 00  90 02 22 00  07 01 00 00  D0 EE 3A 00  F.....".......:.

003AEEB0: 14 F5 3A 00  FE 00 00 00  5C 00 50 00  20 F5 3A 00  ..:.....\.P. .:.

003AEEC0: 67 00 72 00  61 00 6D 00  20 00 46 00  69 00 6C 00  g.r.a.m. .F.i.l.

003AEED0: 41 4C C3 7B  00 00 00 00  FF FF FF FF  03 00 00 00  AL.{............





------------------------------------------------------------------------------

---

### Post by linuxuser21 on 2009-03-10
What guide are you using?

---

### Post by Dreygz on 2009-03-10
uhhh sorry im a total noob to this... what is a guide.?

---

### Post by linuxuser21 on 2009-03-10
The guide that told you how to install & run WoW.

---

### Post by Dreygz on 2009-03-10
I used [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by linuxuser21 on 2009-03-10
Do you know what video card your PC has?

---

### Post by ClaytonOT on 2009-03-10
Did you SET gxApi "OpenGL" ? That solves a lot of problems.

---

### Post by Dreygz on 2009-03-11
nvidia geforce 9800 or somethin like that

---

### Post by Distilled on 2009-03-11
Not that I think you're stupid but have you installed the driver(s) for this video card?

---

### Post by linuxuser21 on 2009-03-11
> **Distilled said:**
> Not that I think you're stupid but have you installed the driver(s) for this video card?

That was going to be my next question. lol.  If not, [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") is how.

---

### Post by Dreygz on 2009-03-11
its ok to think im studip and i did go into the system hardware drivers and install it there? is there anything else to do? and its a nvidia geforce 8600 gt not the other =.= srry

---

### Post by c/Kr3t on 2009-03-11
i used these two pages to get wow to work on ubuntu.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by Dreygz on 2009-03-11
> **ClaytonOT said:**
> Did you SET gxApi "OpenGL" ? That solves a lot of problems.
i tried that but the wtf config file will only appear after you have started the game up once and i can't even get that far.

---

### Post by linuxuser21 on 2009-03-11
Sorry, I've recommended that page to one to many people.  [Here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") is the nVIDIA driver how-to.
Btw, you've got to stop putting yourself down & give yourself a little credit. lol.

---

### Post by thtrgremlin on 2009-03-11
According to your dump log, you did not set the necessary option as mentioned by ClaytonOT

The following will add it:
```
echo 'SET gxApi "OpenGL"' >> /home/taylor/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```

The manual way:
```
gedit /home/taylor/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```
then go to the very end of the file and add the line:
> SET gxApi "OpenGL"

That should get you going. Have fun!

---

### Post by Dreygz on 2009-03-11
kk... thnx i tried to do it manually but the file just wasn't there and i didn't know the code for it thanks everyone.

---

