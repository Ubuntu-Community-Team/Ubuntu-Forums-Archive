---
title: "Uninstall 8.04"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by ex-para on 2009-04-06
How can I safely remove Ubuntu 8.04 from my Laptop. The Laptop an ASUS  Vista was new last December but it has a wide screen and worst of all SIS drives and after many hours of do this and do that I was able to get the correct resolution but as soon as I reboot it reverts back so I have chosen Fatdog 111 as the resolution is near enough and I have been able to download oxyjen openoffice to it and it has Firefox and must be fastest boot up I have seen and warns when the battrey is running out. I have Ubuntu in other Laptops I use working XP as guest and these are OK . When I look at the ASUS hard drive with Gpart I see one part with VistaOS  but the other patitions are not named so I would appreciat any information regarding the uninstall.

---

### Post by dk92123 on 2009-04-06
> **ex-para said:**
> How can I safely remove Ubuntu 8.04 from my Laptop. The Laptop an ASUS  Vista was new last December but it has a wide screen and worst of all SIS drives and after many hours of do this and do that I was able to get the correct resolution but as soon as I reboot it reverts back so I have chosen Fatdog 111 as the resolution is near enough and I have been able to download oxyjen openoffice to it and it has Firefox and must be fastest boot up I have seen and warns when the battrey is running out. I have Ubuntu in other Laptops I use working XP as guest and these are OK . When I look at the ASUS hard drive with Gpart I see one part with VistaOS  but the other patitions are not named so I would appreciat any information regarding the uninstall.

**That first little FAT partition is important, do not delete it.**  it's the OEM info needed for windows. If you only want to delete the linux os, it will probably be just a ext3 and swap leave the rest.

*If you want to do that again with install and uninstall, you may want to consider using Wubi (a Windows App that installs Ubuntu on a VFAT partition on top of your NTFS and uninstalls ubuntu same way you uninstall a win app)

---

