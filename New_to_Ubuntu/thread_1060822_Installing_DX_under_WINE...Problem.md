---
title: "Installing DX under WINE...Problem"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-05
I am trying to install Direct X using WINE and I have encountered an error. I followed these instructions on this site: [http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html) .

I downloaded WINE ok and seems to work fine. I then proceded to load all the dlls manualy (screenshot 1 & 2 below). Then I started the dxsetup like they it said and ran into the error, (screenshot 3 below). 

What did I do wrong?

I am sorry I forgot. This is the terminal output...

leo@Lions-Den:~/DX$  wine DXSETUP.exe
fixme:reg:GetNativeSystemInfo (0x7e3f8700) using GetSystemInfo()
fixme:mscoree:GetCORVersion (0x7e3f82f8, 600, 0x7e3f82e4): semi-stub!
fixme:mscoree:LoadLibraryShim (0xac31f8 L"fusion.dll", (nil), (nil), 0x7e3f7b1c): semi-stub
fixme:fusion:GetCachePath (00000002, L"\10e8", 0x7e3f6a2c) stub!
fixme:fusion:GetCachePath (00000002, L"\3230\302f\2f35\3930\3020\3a35\3730\353a\3a31\6420\7578\6470\7461\3a65\4320\444d\4358\6568\6b63\3a3a\7349\7341\6573\626d\796c\6e49\7355\2865\3a29\4720\7465\7341\6573\626d\796c\694c\7473\2928\6620\6961\656c\2c64\6520\7272\726f\3d20\3020\3878\3030\3430\3030\2e31\0a0d\7e3f\80c1\b7df\def3\b7d5\aff4\7bc8\7364"..., 0x7e3f6a2c) stub!
fixme:fusion:GetCachePath (00000002, L"\3230\302f\2f35\3930\3020\3a35\3730\353a\3a31\6420\7578\6470\7461\3a65\4320\444d\4358\6568\6b63\3a3a\7349\7341\6573\626d\796c\6e49\7355\2865\3a29\4720\7465\7341\6573\626d\796c\694c\7473\2928\6620\6961\656c\2c64\6520\7272\726f\3d20\3020\3878\3030\3430\3030\2e31\0a0d\7e3f\80c1\b7df\def3\b7d5\aff4\7bc8\7364"..., 0x7e3f6a2c) stub!
fixme:fusion:GetCachePath (00000002, L"\3230\302f\2f35\3930\3020\3a35\3730\353a\3a31\6420\7578\6470\7461\3a65\4320\444d\4358\6568\6b63\3a3a\7349\7341\6573\626d\796c\6e49\7355\2865\3a29\4720\7465\7341\6573\626d\796c\694c\7473\2928\6620\6961\656c\2c64\6520\7272\726f\3d20\3020\3878\3030\3430\3030\2e31\0a0d\7e3f\80c1\b7df\def3\b7d5\aff4\7bc8\7364"..., 0x7e3f6a2c) stub!
fixme:fusion:GetCachePath (00000002, L"\3230\302f\2f35\3930\3020\3a35\3730\353a\3a31\6420\7578\6470\7461\3a65\4320\444d\4358\6568\6b63\3a3a\7349\7341\6573\626d\796c\6e49\7355\2865\3a29\4720\7465\7341\6573\626d\796c\694c\7473\2928\6620\6961\656c\2c64\6520\7272\726f\3d20\3020\3878\3030\3430\3030\2e31\0a0d\7e3f\80c1\b7df\def3\b7d5\aff4\7bc8\7364"..., 0x7e3f6a2c) stub!
fixme:fusion:GetCachePath (00000002, L"\3230\302f\2f35\3930\3020\3a35\3730\353a\3a31\6420\7578\6470\7461\3a65\4320\444d\4358\6568\6b63\3a3a\7349\7341\6573\626d\796c\6e49\7355\2865\3a29\4720\7465\7341\6573\626d\796c\694c\7473\2928\6620\6961\656c\2c64\6520\7272\726f\3d20\3020\3878\3030\3430\3030\2e31\0a0d\7e3f\80c1\b7df\def3\b7d5\aff4\7bc8\7364"..., 0x7e3f6a2c) stub!
fixme:fusion:GetCachePath (00000002, L"\3230\302f\2f35\3930\3020\3a35\3730\353a\3a31\6420\7578\6470\7461\3a65\4320\444d\4358\6568\6b63\3a3a\7349\7341\6573\626d\796c\6e49\7355\2865\3a29\4720\7465\7341\6573\626d\796c\694c\7473\2928\6620\6961\656c\2c64\6520\7272\726f\3d20\3020\3878\3030\3430\3030\2e31\0a0d\7e3f\80c1\b7df\def3\b7d5\aff4\7bc8\7364"..., 0x7e3f6a2c) stub!
fixme:fusion:GetCachePath (00000002, L"\3230\302f\2f35\3930\3020\3a35\3730\353a\3a31\6420\7578\6470\7461\3a65\4320\444d\4358\6568\6b63\3a3a\7349\7341\6573\626d\796c\6e49\7355\2865\3a29\4720\7465\7341\6573\626d\796c\694c\7473\2928\6620\6961\656c\2c64\6520\7272\726f\3d20\3020\3878\3030\3430\3030\2e31\0a0d\7e3f\80c1\b7df\def3\b7d5\aff4\7bc8\7364"..., 0x7e3f6a2c) stub!
fixme:fusion:GetCachePath (00000002, L"\3230\302f\2f35\3930\3020\3a35\3730\353a\3a31\6420\7578\6470\7461\3a65\4320\444d\4358\6568\6b63\3a3a\7349\7341\6573\626d\796c\6e49\7355\2865\3a29\4720\7465\7341\6573\626d\796c\694c\7473\2928\6620\6961\656c\2c64\6520\7272\726f\3d20\3020\3878\3030\3430\3030\2e31\0a0d\7e3f\80c1\b7df\def3\b7d5\aff4\7bc8\7364"..., 0x7e3f6a2c) stub!
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 140 requests (140 known processed) with 0 events remaining.
leo@Lions-Den:~/DX$

---

### Post by Voland on 2009-02-05
Have you read comments to orig. message?

---

