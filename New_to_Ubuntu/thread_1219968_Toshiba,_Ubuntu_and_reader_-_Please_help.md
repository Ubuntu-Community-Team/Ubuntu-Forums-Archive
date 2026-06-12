---
title: "Toshiba, Ubuntu and reader - Please help"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by ketedford on 2009-07-22
Hello All --
I am about 2 weeks in to now using Ubuntu 9.04 with all current updates. Wiped out Windows and hope to never look back. Looking for some guru to help me out.

I have a Toshiba A135-S4656.

1) I can not get my SD Reader to work. Nothing happens at all when I insert media. I can not open it.

As other people have done, I have run the**  lshal | grep SD** and get:

  info.product = 'PCIxx12 SDA Standard Compliant SD Host Controller'  (string)
  pci.product = 'PCIxx12 SDA Standard Compliant SD Host Controller'  (string)
  info.product = 'MMC/SD Host Adapter'  (string)
  info.product = '5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)'  (string)
  pci.product = '5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)'  (string)
eric@eric-laptop:~$

**Also ran dmesg | tail -n20**

eric@eric-laptop:~$ dmesg | tail -n20
[109656.185122] [drm:i915_getparam] *ERROR* Unknown parameter 6
[110256.187879] [drm:i915_getparam] *ERROR* Unknown parameter 6
[112595.141191] [drm:i915_getparam] *ERROR* Unknown parameter 6
[112595.610604] [drm:i915_getparam] *ERROR* Unknown parameter 6
[113195.417579] [drm:i915_getparam] *ERROR* Unknown parameter 6
[113795.276925] [drm:i915_getparam] *ERROR* Unknown parameter 6
[114395.300377] [drm:i915_getparam] *ERROR* Unknown parameter 6
[116111.747622] [drm:i915_getparam] *ERROR* Unknown parameter 6
[116112.031367] [drm:i915_getparam] *ERROR* Unknown parameter 6
[116711.813641] [drm:i915_getparam] *ERROR* Unknown parameter 6
[117311.833547] [drm:i915_getparam] *ERROR* Unknown parameter 6
[117911.818486] [drm:i915_getparam] *ERROR* Unknown parameter 6
[119006.567658] [drm:i915_getparam] *ERROR* Unknown parameter 6
[119006.889900] [drm:i915_getparam] *ERROR* Unknown parameter 6
[119606.634921] [drm:i915_getparam] *ERROR* Unknown parameter 6
[120206.654191] [drm:i915_getparam] *ERROR* Unknown parameter 6
[120806.638392] [drm:i915_getparam] *ERROR* Unknown parameter 6
[126168.100028] tifm_core: MemoryStick card detected in socket 0:0
[126199.910759] tifm0 : demand removing card from socket 0:0
[126220.652030] tifm_core: MemoryStick card detected in socket 0:0
eric@eric-laptop:~$

---

### Post by esalnoj on 2009-07-22
You card reader is showing up, but...

Do you have a "fatal-modprobe couldn't load module.dep" error at boot-up?

That was preventing my card reader from working on my Gateway laptop.

---

