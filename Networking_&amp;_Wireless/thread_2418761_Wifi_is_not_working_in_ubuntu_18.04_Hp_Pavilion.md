---
title: "Wifi is not working in ubuntu 18.04 Hp Pavilion"
date: 2019-05-11
forum: Networking &amp; Wireless
---

### Post by heberley on 2019-05-11
If I type 

```

lspci -nn -d 14e4:

```

Then I got
```

08:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)

```

If I try to reinstall the driver I got a weird message
```

sudo apt-get purge bcmwl-kernel-source

```
the output is
```

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  bcmwl-kernel-source*
0 actualizados, 0 nuevos se instalarán, 1 para eliminar y 263 no actualizados.
Se liberarán 8.067 kB después de esta operación.
¿Desea continuar? [S/n] s
(Leyendo la base de datos ... 204356 ficheros o directorios instalados actualmente.)
Desinstalando bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Procesando disparadores para initramfs-tools (0.130ubuntu3.6) ...
update-initramfs: Generating /boot/initrd.img-4.18.0-18-generic
W: Possible missing firmware /lib/firmware/nvidia/gv100/sec2/sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/sec2/image.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/sec2/desc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/nvdec/scrubber.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/sw_method_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/sw_bundle_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/sw_nonctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/sw_ctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/gpccs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/gpccs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/fecs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/fecs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/acr/ucode_load.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/acr/unload_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/acr/bl.bin for module nouveau
I: The initramfs will attempt to resume from /dev/sda5
I: (UUID=86c38339-2541-40a6-860a-f2134372cd66)
I: Set the RESUME variable to override this.
(Leyendo la base de datos ... 204270 ficheros o directorios instalados actualmente.)
Purgando ficheros de configuración de bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
update-initramfs: deferring update (trigger activated)
Procesando disparadores para initramfs-tools (0.130ubuntu3.6) ...
update-initramfs: Generating /boot/initrd.img-4.18.0-18-generic
W: Possible missing firmware /lib/firmware/nvidia/gv100/sec2/sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/sec2/image.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/sec2/desc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/nvdec/scrubber.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/sw_method_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/sw_bundle_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/sw_nonctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/sw_ctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/gpccs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/gpccs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/fecs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/fecs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/acr/ucode_load.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/acr/unload_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gv100/acr/bl.bin for module nouveau
I: The initramfs will attempt to resume from /dev/sda5
I: (UUID=86c38339-2541-40a6-860a-f2134372cd66)
I: Set the RESUME variable to override this.

```

Even If I reinstall it the wifi does not work

---

### Post by praseodym on 2019-05-11
Try
```

sudo apt-get install --reinstall linux-firmware broadcom-sta-dkms dkms build-essential
```
Reboot and deactivate SecureBoot

---

