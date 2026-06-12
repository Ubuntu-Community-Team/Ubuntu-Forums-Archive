---
title: "issues - Dreamweaver installation using wine/winetricks"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Rackz on 2011-03-15
I tried to install Dreamweaver CS3 using wine1.2 in ubuntu 10.10. But I received few error messages as shown below

fixme:win:EnumDisplayDevicesW ((null),0,0x32f720,0x00000000), stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x192614 0x192620 0x1929a0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x192614 0x192620 0x192908 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x192614 0x192620 0x192908 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x192614 0x192620 0x192908 (nil)


I search for the solution and in some forums it has been said that these errors appear when older version of wine is used which does not support certain files (or whatever it is said)

so i upgrade wine 1.2 to 1.3 and tried again but still the error appears. But in both the cases it seems that the dreamweaver is opened with an alert box showing no message( only titled as 'Adobe'). I have attached the screenshot of the alert box that i got.

Can anybody help me to fix this?

---

