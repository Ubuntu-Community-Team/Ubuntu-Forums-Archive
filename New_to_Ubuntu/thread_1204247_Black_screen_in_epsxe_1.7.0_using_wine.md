---
title: "Black screen in epsxe 1.7.0 using wine"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by Melhisedek on 2009-07-04
Hello there,
just installed latest wine 1.1.25 and wanted to get epsxe to work. Sadly I only get black screen. Sound is playing in the background and I can my guy walking around and pressing stuff so gamepad is working as well, but graphics arent. I have tried GPUPeteXGL2 and normal GL.

Any ideas?

Here is wine output:
```

 * Running ePSXe emulator version 1.7.0. 
 * Running ePSXe emulator version 1.7.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [bios\scph1001.bin]. 
 * Loading ISO Format [MDF/BIN/IMG2352] (+subchannel) ok
 * First/Last track: 1 1
 * Track 1: (DATA)  - Start 1: (00,02,00) -  Length 65:03
 * NTSC cdrom detected. (SLUS_012.95) 
 * Doing init gpu[0]... 
err:wgl:X11DRV_wglShareLists Could not share display lists, context already created !
 * Gpu open[0]... 
 * Direct input init ok. 
 * Doing spu init... 
 * Spu open... 
 * LoadState Done! 
 * Closing spu ... 
 * Shutdown gpu ...
 * Closing ISO system.
```

---

### Post by Melhisedek on 2009-07-05
Is there any "ground" setup of wine I need to do?

---

