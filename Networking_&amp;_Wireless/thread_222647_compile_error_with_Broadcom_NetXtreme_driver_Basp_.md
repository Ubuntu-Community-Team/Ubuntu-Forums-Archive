---
title: "compile error with Broadcom NetXtreme driver /Basp software (Copper-Link)"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by hurr1k4ne on 2006-07-25
Hey i'm new to Linux and Ubuntu...

I like it much atm, but now i got stucked again...

I have two 3Com GigabitNIC in my server...

Installed Ubuntu 6.06 Server. afterwards loaded ubuntu-desktop

the NIC works well, but i want to use load balancing capatibilities  
with normally is provided by Broadcom BASP-Software...

**[SIZE="4"][COLOR="Red"]Is there a Linux/ubuntu way to provide load balancing???[/COLOR][/SIZE]**

Broadcom has a source package of the driver and the software.
I downloaded them and copied them to usr/src

after trying to get kernel sources, i now have those dirs in usr/src :-D 

bcm5700-6.0.2 <<Broadcom dirver src
linux link to linux-headers-2.6.15-26
linux-headers-2.6.15-26
linux-headers-2.6.15-26-server
linux-source-2.6.15
ubuntu-2.6

when i CD to usr/src/bcm5700-6.0.2/src/ and type make it gives me a lot of errors...(attached at end)

Can anyone please tell me my mistake, so i don't need to spend my days on trying to compile things??



root@ubfl-server:/usr/src/bcm5700-6.0.2/src# make
gcc -DMODULE -D__KERNEL__ -DDBG=0 -DT3_JUMBO_RCV_RCB_ENTRY_COUNT=256 -DNICE_SUPPORT -DPCIX_TARGET_WORKAROUND=1 -DINCLUDE_TBI_SUPPORT -DINCLUDE_5701_AX_FIX=1 -Wall -Wstrict-prototypes -O6 -I/lib/modules/`uname -r`/build/include   -c -o b57um.o b57um.c
In Datei, eingefügt von b57um.c:19:
mm.h:30:31: Fehler: linux/modversions.h: No such file or directory
In file included from /lib/modules/2.6.15-26-server/build/include/asm/processor.h:18,
                 from /lib/modules/2.6.15-26-server/build/include/asm/thread_info.h:17,
                 from /lib/modules/2.6.15-26-server/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.15-26-server/build/include/linux/preempt.h:10,
                 from /lib/modules/2.6.15-26-server/build/include/linux/spinlock.h:50,
                 from /lib/modules/2.6.15-26-server/build/include/linux/capability.h:45,
                 from /lib/modules/2.6.15-26-server/build/include/linux/sched.h:7,
                 from /lib/modules/2.6.15-26-server/build/include/linux/module.h:10,
                 from mm.h:32,
                 from b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/asm/system.h: In Funktion »__set_64bit_var«:
/lib/modules/2.6.15-26-server/build/include/asm/system.h:213: Warnung: Dereferenzierung eines Type-Pun-Zeigers verletzt strict-aliasing-Regeln
/lib/modules/2.6.15-26-server/build/include/asm/system.h:213: Warnung: Dereferenzierung eines Type-Pun-Zeigers verletzt strict-aliasing-Regeln
In Datei, eingefügt von /lib/modules/2.6.15-26-server/build/include/asm/smp.h:18,
                    von /lib/modules/2.6.15-26-server/build/include/linux/smp.h:19,
                    von /lib/modules/2.6.15-26-server/build/include/linux/sched.h:26,
                    von /lib/modules/2.6.15-26-server/build/include/linux/module.h:10,
                    von mm.h:32,
                    von b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/asm/mpspec.h:6:25: Fehler: mach_mpspec.h: No such file or directory
In file included from /lib/modules/2.6.15-26-server/build/include/asm/smp.h:18,
                 from /lib/modules/2.6.15-26-server/build/include/linux/smp.h:19,
                 from /lib/modules/2.6.15-26-server/build/include/linux/sched.h:26,
                 from /lib/modules/2.6.15-26-server/build/include/linux/module.h:10,
                 from mm.h:32,
                 from b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/asm/mpspec.h: Auf höchster Ebene:
/lib/modules/2.6.15-26-server/build/include/asm/mpspec.h:8: Fehler: »MAX_MP_BUSSES« ist hier nicht deklariert (nicht in einer Funktion)
/lib/modules/2.6.15-26-server/build/include/asm/mpspec.h:23: Fehler: »MAX_IRQ_SOURCES« ist hier nicht deklariert (nicht in einer Funktion)
In Datei, eingefügt von /lib/modules/2.6.15-26-server/build/include/linux/smp.h:19,
                    von /lib/modules/2.6.15-26-server/build/include/linux/sched.h:26,
                    von /lib/modules/2.6.15-26-server/build/include/linux/module.h:10,
                    von mm.h:32,
                    von b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/asm/smp.h:77:26: Fehler: mach_apicdef.h: No such file or directory
In file included from /lib/modules/2.6.15-26-server/build/include/linux/smp.h:19,
                 from /lib/modules/2.6.15-26-server/build/include/linux/sched.h:26,
                 from /lib/modules/2.6.15-26-server/build/include/linux/module.h:10,
                 from mm.h:32,
                 from b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/asm/smp.h: In Funktion »hard_smp_processor_id«:
/lib/modules/2.6.15-26-server/build/include/asm/smp.h:81: Warnung: implizite Deklaration der Funktion »GET_APIC_ID«
In Datei, eingefügt von /lib/modules/2.6.15-26-server/build/include/linux/irq.h:22,
                    von /lib/modules/2.6.15-26-server/build/include/asm/hardirq.h:6,
                    von /lib/modules/2.6.15-26-server/build/include/linux/hardirq.h:7,
                    von /lib/modules/2.6.15-26-server/build/include/linux/interrupt.h:11,
                    von mm.h:47,
                    von b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/asm/irq.h:16:25: Fehler: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.15-26-server/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.15-26-server/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.15-26-server/build/include/linux/interrupt.h:11,
                 from mm.h:47,
                 from b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/linux/irq.h: Auf höchster Ebene:
/lib/modules/2.6.15-26-server/build/include/linux/irq.h:85: Fehler: »NR_IRQS« ist hier nicht deklariert (nicht in einer Funktion)
In file included from /lib/modules/2.6.15-26-server/build/include/linux/irq.h:94,
                 from /lib/modules/2.6.15-26-server/build/include/asm/hardirq.h:6,
                 from /lib/modules/2.6.15-26-server/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.15-26-server/build/include/linux/interrupt.h:11,
                 from mm.h:47,
                 from b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/asm/hw_irq.h:30: Fehler: »NR_IRQ_VECTORS« ist hier nicht deklariert (nicht in einer Funktion)
In file included from /lib/modules/2.6.15-26-server/build/include/linux/if_ether.h:109,
                 from /lib/modules/2.6.15-26-server/build/include/linux/netdevice.h:29,
                 from mm.h:50,
                 from b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/linux/skbuff.h: In Funktion »skb_add_data«:
/lib/modules/2.6.15-26-server/build/include/linux/skbuff.h:1128: Warnung: Zeigerziele bei Übergabe des Arguments 1 von »csum_and_copy_from_user« unterscheiden sich im Vorzeichenbesitz
In file included from /lib/modules/2.6.15-26-server/build/include/net/request_sock.h:22,
                 from /lib/modules/2.6.15-26-server/build/include/linux/ip.h:84,                 from /lib/modules/2.6.15-26-server/build/include/net/ip.h:28,
                 from mm.h:76,
                 from b57um.c:19:
/lib/modules/2.6.15-26-server/build/include/net/sock.h: In Funktion »skb_copy_to_page«:
/lib/modules/2.6.15-26-server/build/include/net/sock.h:1064: Warnung: Zeigerziele bei Übergabe des Arguments 1 von »csum_and_copy_from_user« unterscheiden sich im Vorzeichenbesitz
b57um.c: In Funktion »bcm5700_init_board«:
b57um.c:614: Warnung: implizite Deklaration der Funktion »init_etherdev«
b57um.c:614: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
b57um.c: In Funktion »bcm5700_open«:
b57um.c:964: Warnung: Übergabe des Arguments 2 von »request_irq« von inkompatiblem Zeigertyp
b57um.c: In Funktion »netdev_ethtool_ioctl«:
b57um.c:1796: Fehler: »struct pci_dev« hat kein Element namens »slot_name«
b57um.c: Auf höchster Ebene:
b57um.c:2603: Warnung: Initialisierung von inkompatiblem Zeigertyp
b57um.c: In Funktion »MM_GetConfig«:
b57um.c:2905: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
b57um.c:2909: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
b57um.c:2914: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
b57um.c:2923: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
b57um.c:2928: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
b57um.c:2944: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
b57um.c:2952: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
b57um.c:2966: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
b57um.c:2973: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »bcm5700_validate_param_range« unterscheiden sich im Vorzeichenbesitz
make: *** [b57um.o] Fehler 1

---

### Post by philippe_carlo on 2006-07-25
Install the kernel headers.

---

### Post by hurr1k4ne on 2006-07-25
wow.. damn fast answer... THX alot....

hmm.. when i do apt-get install linux-headers-2.6.15-26 it says
aleardy newest version..

when i try /usr/src/linux-headers[..]/make
it stops with error 2 
sth. about:
no rule known, to create target "init/main.o", needed from "init/built-in.o"

is it right i ln 'd the linux-headers to linux????

---

### Post by hurr1k4ne on 2006-07-25
I've found instruction to build new kernel which writes about header files....

so i've done 
make-kpkg --initrd --append-to-version=-custom kernel_headers

(but nothing before)

it stops with an error....


install: Aufruf von stat für „CREDITS“ nicht möglich: No such file or directory
make[1]: *** [real_stamp_headers] Fehler 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26'
make: *** [stamp-headers] Fehler 2


*sigh* there sth crappy around here.... ](*,) :-k

---

