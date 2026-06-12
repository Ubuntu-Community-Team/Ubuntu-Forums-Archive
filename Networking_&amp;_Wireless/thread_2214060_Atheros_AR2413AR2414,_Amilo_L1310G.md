---
title: "Atheros AR2413/AR2414, Amilo L1310G"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by AmIL0 on 2014-03-30
Hello,

):P
I am new user to Ubuntu/Linux... coming from WIN XP now at the end of MS support.

I try to make WIFI card from my ( old and still working ) Amilo L1310G to work as instructed here:

 [http://ubuntuforums.org/showthread.php?t=1530962](http://ubuntuforums.org/showthread.php?t=1530962)

but because of this 13.10 -13.11 version I am testing now, I get this errors:

```

make -C /lib/modules/3.11.0-19-generic/build SUBDIRS=/home/amilo/Documents/fsaa1655g-kernel-2.6.26 modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-19-generic'
  CC [M]  /home/amilo/Documents/fsaa1655g-kernel-2.6.26/fsaa1655g.o
/home/amilo/Documents/fsaa1655g-kernel-2.6.26/fsaa1655g.c: In function ‘amiloa1655g_proc_init’:
/home/amilo/Documents/fsaa1655g-kernel-2.6.26/fsaa1655g.c:157:2: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
  dir_base = create_proc_entry(DRV_NAME, S_IFDIR, NULL);
  ^
/home/amilo/Documents/fsaa1655g-kernel-2.6.26/fsaa1655g.c:157:11: warning: assignment makes pointer from integer without a cast [enabled by default]
  dir_base = create_proc_entry(DRV_NAME, S_IFDIR, NULL);
           ^
/home/amilo/Documents/fsaa1655g-kernel-2.6.26/fsaa1655g.c:166:6: warning: assignment makes pointer from integer without a cast [enabled by default]
  ent = create_proc_entry("radio", S_IFREG | S_IRUGO | S_IWUSR, 
      ^
/home/amilo/Documents/fsaa1655g-kernel-2.6.26/fsaa1655g.c:169:6: error: dereferencing pointer to incomplete type
   ent->read_proc = proc_get_radio;
      ^
/home/amilo/Documents/fsaa1655g-kernel-2.6.26/fsaa1655g.c:170:6: error: dereferencing pointer to incomplete type
   ent->write_proc = proc_set_radio;
      ^
cc1: some warnings being treated as errors
make[2]: *** [/home/amilo/Documents/fsaa1655g-kernel-2.6.26/fsaa1655g.o] Error 1
make[1]: *** [_module_/home/amilo/Documents/fsaa1655g-kernel-2.6.26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-19-generic'
make: *** [default] Error 2


```

source are from here
[URL="http://marvec.org/amilo/"]
http://marvec.org/amilo/[/URL]

I have no idea what need to be changed in source to be able to make & install in this new kernel;
 anybody who can help ?

Thank you.
L.

---

### Post by mörgæs on 2014-03-30
Hi, welcome to the fora.
The thread to which you are linking is ancient and should not be used. Please begin with running the commands shown here:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by AmIL0 on 2014-03-30
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC410 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 11)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge
00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RC410M [Mobility Radeon Xpress 200M]
02:01.0 Ethernet controller: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01)
02:0b.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:0b.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:0b.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:0b.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:0d.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

```
Bus 001 Device 002: ID 0bc2:3320 Seagate RSS LLC SRD00F2 [Expansion Desktop Drive]
Bus 001 Device 005: ID 1e4e:0103 Cubeternet 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 15d9:0a4d Trust International B.V. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
Module                  Size  Used by
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
snd_usb_audio         119227  1 
videodev              107508  2 uvcvideo,videobuf2_core
snd_usbmidi_lib        24326  1 snd_usb_audio
snd_hwdep              13272  1 snd_usb_audio
joydev                 17097  0 
arc4                   12536  2 
ip6t_REJECT            12826  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
nf_conntrack_ipv6      18414  7 
nf_defrag_ipv6         26070  1 nf_conntrack_ipv6
ipt_REJECT             12485  1 
xt_LOG                 17446  10 
xt_limit               12541  13 
xt_tcpudp              12756  22 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  7 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  14 
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
parport_pc             31981  0 
nf_nat                 25588  1 nf_nat_ftp
nf_conntrack_ftp       14056  1 nf_nat_ftp
ppdev                  17391  0 
nf_conntrack           82913  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
bnep                   18959  2 
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
rfcomm                 53664  0 
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
ath5k                 135055  0 
bluetooth             323656  10 bnep,rfcomm
radeon               1312332  2 
ath                    19187  1 ath5k
mac80211              517444  1 ath5k
microcode              18894  0 
pcmcia                 51368  0 
ttm                    75982  1 radeon
cfg80211              401762  3 ath,ath5k,mac80211
drm_kms_helper         46867  1 radeon
psmouse                90642  0 
serio_raw              13189  0 
yenta_socket           40193  0 
drm                   242400  4 ttm,drm_kms_helper,radeon
snd_atiixp             19264  2 
tifm_7xx1              13163  0 
snd_atiixp_modem       18629  0 
pcmcia_rsrc            18319  1 yenta_socket
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
tifm_core              15040  1 tifm_7xx1
snd_rawmidi            25094  2 snd_usbmidi_lib,snd_seq_midi
snd_ac97_codec        105668  2 snd_atiixp_modem,snd_atiixp
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
ac97_bus               12642  1 snd_ac97_codec
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_pcm                89488  4 snd_usb_audio,snd_ac97_codec,snd_atiixp_modem,snd_atiixp
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         14230  3 snd_pcm,snd_atiixp_modem,snd_atiixp
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  18 snd_usb_audio,snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_seq_device,snd_atiixp_modem,snd_atiixp,snd_seq_midi
soundcore              12600  1 snd
i2c_algo_bit           13197  1 radeon
shpchp                 32129  0 
mac_hid                13037  0 
i2c_piix4              17682  0 
ati_agp                13177  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
pata_acpi              12886  0 
usb_storage            48294  1 
b44                    31234  0 
firewire_ohci          35463  0 
sdhci_pci              18456  0 
ssb                    51596  1 b44
firewire_core          57656  1 firewire_ohci
mii                    13654  1 b44
crc_itu_t              12627  1 firewire_core
sdhci                  37644  1 sdhci_pci
pata_atiixp            13058  1 

```

```
Description:    Ubuntu 13.10
3.11.0-19-generic i686

```

---

### Post by mörgæs on 2014-03-31
Does this help? 
[https://sites.google.com/site/opensourcefreesoftwarewiki/hardware/qualcomm-atheros-ar2413-ar2414-ar5005g-s-wireless-adapter](https://sites.google.com/site/opensourcefreesoftwarewiki/hardware/qualcomm-atheros-ar2413-ar2414-ar5005g-s-wireless-adapter)

---

### Post by AmIL0 on 2014-03-31
Of course it not working...

>  This laptop uses a wifi enabled by a button not controlled by hardware.
 Because of this, you get a wifi working with no antenna.
 You need two things: enable the rfkill=0 option for the ath_pci module from the atheros driver, and then, activate the wifi as it was enabled by pression the button, using a module that one guy (BIG THANK YOU! to Martin Vecera) made for the A1655G fujitsu laptop, that also works on the l1310g. 

as explayned here: [https://wiki.ubuntu.com/LaptopTestingTeam/Old/FujitsuAmiloL1310G](https://wiki.ubuntu.com/LaptopTestingTeam/Old/FujitsuAmiloL1310G)

---

### Post by jeje_louvetou on 2014-04-03
Hello I do have the same problem - I directly contacted the developer of the fsaa1655g driver who doesn't have an amilo laptop anymore :-(, and posted a request for help here [http://forums.linuxmint.com/viewtopic.php?f=49&t=154495](http://forums.linuxmint.com/viewtopic.php?f=49&t=154495)

Any help would be greatly appreciated :)

---

### Post by Ronald_van_Dijk on 2014-04-18
Based upon [http://ubuntuforums.org/showthread.php?t=1530962](http://ubuntuforums.org/showthread.php?t=1530962) I modified the fsaa1655g.c to make it compatible with the 3.11 kernel. The following works on Xubuntu 13.10 (Kernel 3.11.0-19-generic):

 ```

/***************************************************************************
 *   Copyright (C) 2005 by Alejandro Vidal Mata & Javier Vidal Mata        *
 *                                                                         *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 *                                                                         *
 *   The full GNU General Public License is included in this distribution  *
 *   in the file called COPYING.                                           *
 *                                                                         *
 *   This project haven't a warranty. The project developers haven't       *
 *   responsible for whatever happens from using.                          *
 *                                                                         *
 *   Author:                                                               *
 *    Martin Vecera <ja@marvec.org>                                        *
 *                                                                         *
 *   Based on fsam7440 by:                                                 *
 *    Alejandro Vidal Mata <alex14@gmail.com>                              *
 *    Javier Vidal Mata <javitu@gmail.com>                                 *
 *                                                                         *
 *   Based on:                                                             *
 *    pbe5.c by Pedro Ramalhais <pmr09313@students.fct.unl.pt>             *
 *                                       *
 *                                       *
 *   Modified on 18-04-2014 by Ronald van Dijk: r.van.dijk@pl.hanze.nl     *
 *   to make compatible with 3.11 kernel. Tested on Xubuntu 13.10.         *
 ***************************************************************************/


#include <linux/compiler.h>
#include <linux/errno.h>
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/types.h>
#include <linux/netdevice.h>
#include <linux/version.h>
#include <linux/proc_fs.h>
#include <asm/uaccess.h>
#include <asm/io.h>

#define DRV_NAME        "fsaa1655g"
#define DRV_VERSION        "1.0"
#define DRV_DESCRIPTION        "SW RF kill switch for Fujitsu-Siemens AMILO A1655G"
#define DRV_AUTHOR        "Martin Vecera"
#define DRV_LICENSE        "GPL"

static int radio = 1;

#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,0)

MODULE_PARM(radio, "i");

#else /* LINUX_VERSION_CODE < 2.6.0 */

#include <linux/moduleparam.h>
module_param(radio, int, 1);

#endif /* LINUX_VERSION_CODE < 2.6.0 */

MODULE_PARM_DESC(radio, "Controls state of radio when the module is loaded (1=on, 0=off)");

MODULE_DESCRIPTION(DRV_DESCRIPTION);
MODULE_AUTHOR(DRV_AUTHOR);
MODULE_LICENSE(DRV_LICENSE);

/*
 * These values were obtained from disassembling and debugging the PM.exe program
 * installed in the Fujitsu-Siemens AMILO A1655G
 */
#define KBD_STATE_PORT      0x64
#define KBD_COMMAND_PORT        0x64
#define KBD_DATA_PORT           0x60

#define WIFI_COMMAND            0xC5
#define WIFI_ON                 0x25
#define WIFI_OFF                0x45

#define AMILOA1655G_RADIO_OFF    0
#define AMILOA1655G_RADIO_ON    1

static int amiloa1655g_radio_status = AMILOA1655G_RADIO_OFF;

unsigned char amiloa1655g_get_radio(void) {
  return amiloa1655g_radio_status;
}

static void amiloa1655g_set_radio(int state_set) {
  unsigned char val = 0;

  if (amiloa1655g_radio_status != state_set) { 
    if (state_set == AMILOA1655G_RADIO_ON) { 
      do { val = inb(KBD_STATE_PORT); } while ((val & 2) == 2);
      outb(WIFI_COMMAND, KBD_COMMAND_PORT);
      do { val = inb(KBD_STATE_PORT); } while ((val & 2) == 2);
      outb(WIFI_ON, KBD_DATA_PORT);
      amiloa1655g_radio_status = AMILOA1655G_RADIO_ON;
      printk(KERN_INFO DRV_NAME ": Radio turned ON\n");
    } else {
      do { val = inb(KBD_STATE_PORT); } while ((val & 2) == 2);
      outb(WIFI_COMMAND, KBD_COMMAND_PORT);
      do { val = inb(KBD_STATE_PORT); } while ((val & 2) == 2);
      outb(WIFI_OFF, KBD_DATA_PORT);
      amiloa1655g_radio_status = AMILOA1655G_RADIO_OFF;
      printk(KERN_INFO DRV_NAME ": Radio turned OFF\n");
    }
  }
}


/*
 * Proc Stuff
 */
static struct proc_dir_entry *dir_base = NULL;




static ssize_t
proc_set_radio(struct file *file, const char __user *buffer, size_t len, loff_t * off)
{
     amiloa1655g_set_radio(buffer[0] == '0' ? AMILOA1655G_RADIO_OFF : AMILOA1655G_RADIO_ON);
    
    return len;
}


static ssize_t proc_get_radio(struct file *filp,    /* see include/linux/fs.h   */
                 char __user *buffer,    /* buffer to fill with data */
                 size_t length,    /* length of the buffer     */
                 loff_t *offset)
{
    int len = 0;
    
    len += snprintf(buffer, length, DRV_NAME ": %d\n", 
            amiloa1655g_radio_status == AMILOA1655G_RADIO_OFF ? 0 : 1);
    
    *offset = 1; 
    return len;
}

static struct file_operations amilo_fops = {
 .read = proc_get_radio,
 .write = proc_set_radio,
};


static void amiloa1655g_proc_cleanup(void)
{
    if (dir_base) {
        remove_proc_entry("radio", dir_base);
        remove_proc_entry(DRV_NAME, NULL);
        dir_base = NULL;
    }
}


static int amiloa1655g_proc_init(void)
{
    struct proc_dir_entry *ent;
    int err = 0;

    /*dir_base = create_proc_entry(DRV_NAME, S_IFDIR, NULL);*/
    dir_base = proc_create(DRV_NAME, S_IFDIR, NULL, &amilo_fops);
    if (dir_base == NULL) {
        printk(KERN_ERR DRV_NAME ": Unable to initialise /proc/" 
               DRV_NAME "\n");
        err = -ENOMEM;
        goto fail;
    }


    /*ent = create_proc_entry("radio", S_IFREG | S_IRUGO | S_IWUSR, 
                dir_base);*/

    ent = proc_create("radio", S_IFREG | S_IRUGO | S_IWUSR, 
                dir_base, &amilo_fops); 
    if (ent == NULL) {
        printk(KERN_ERR
               "Unable to initialize /proc/" DRV_NAME "/radio\n");
        err = -ENOMEM;
        goto fail;
    }

    return 0;

 fail:
    amiloa1655g_proc_cleanup();
    return err;
}

/*
 * module stuff
 */
static int __init amiloa1655g_init(void)
{
    amiloa1655g_proc_init();

    amiloa1655g_set_radio((radio == 1) ? AMILOA1655G_RADIO_ON : AMILOA1655G_RADIO_OFF);
    
    return 0;
}

static void __exit amiloa1655g_exit(void)
{
    amiloa1655g_set_radio(AMILOA1655G_RADIO_OFF);

    amiloa1655g_proc_cleanup();
}

module_init(amiloa1655g_init);
module_exit(amiloa1655g_exit);




```

---

### Post by jeje_louvetou on 2014-04-21
Thank you Ronald, this worked perfectly :-) Thank you so much, sincerely - you are a magician! :-)

---

### Post by marvec2 on 2014-05-06
Hello Ronald,

thank you for updating the driver. I will place it to sourceforge. Let me know the changes you would like to add to the header and authors file to properly list your name and contact.

Thanks,
Martin

---

