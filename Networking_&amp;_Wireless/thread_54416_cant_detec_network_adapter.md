---
title: "cant detec network adapter"
date: 2005-08-04
forum: Networking &amp; Wireless
---

### Post by fedex_08 on 2005-08-04
i must admit i am a newb and i cant detect my network adapter. I unzipped the driver that came with the adapter and made a #make all as described in a readme.txt but this is what i get

gcc -D__KERNEL__ -DMODULE -O -Wall -Wstrict-prototypes -I/usr/include -DUSE_IO_O PS  -D_COMPAT_WITH_OLD_KERNEL   -c -o sundance_main.o sundance_main.c
En el fichero incluído de /usr/include/asm/smp.h:18,
                 de /usr/include/linux/smp.h:17,
                 de /usr/include/linux/sched.h:23,
                 de /usr/include/linux/module.h:10,
                 de sundance_main.c:168:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No existe el fichero o el directo rio
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from sundance_main.c:168:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a fu nction)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a fu nction)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a f unction)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a f unction)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a funct ion)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a f unction)
/usr/include/asm/mpspec.h:20: error: conflicting types for `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:8: error: previous declaration of `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:22: error: `MAX_IRQ_SOURCES' undeclared here (not in a  function)
/usr/include/asm/mpspec.h:24: error: `MAX_MP_BUSSES' undeclared here (not in a f unction)
/usr/include/asm/mpspec.h:24: error: conflicting types for `mp_bus_id_to_pci_bus '
/usr/include/asm/mpspec.h:12: error: previous declaration of `mp_bus_id_to_pci_b us'
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a funct ion)
In file included from /usr/include/asm/smp.h:20,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from sundance_main.c:168:
/usr/include/asm/io_apic.h:120: error: `MAX_IRQ_SOURCES' undeclared here (not in  a function)
/usr/include/asm/io_apic.h:120: error: conflicting types for `mp_irqs'
/usr/include/asm/mpspec.h:22: error: previous declaration of `mp_irqs'
En el fichero incluído de /usr/include/linux/smp.h:17,
                 de /usr/include/linux/sched.h:23,
                 de /usr/include/linux/module.h:10,
                 de sundance_main.c:168:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No existe el fichero o el director io
En el fichero incluído de /usr/include/linux/irq.h:20,
                 de /usr/include/asm/hardirq.h:6,
                 de /usr/include/linux/interrupt.h:11,
                 de sundance_main.c:175:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No existe el fichero o el directori o
In file included from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from sundance_main.c:175:
/usr/include/linux/irq.h:70: error: `NR_IRQS' undeclared here (not in a function )
In file included from /usr/include/linux/irq.h:72,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from sundance_main.c:175:
/usr/include/asm/hw_irq.h:28: error: `NR_IRQS' undeclared here (not in a functio n)
/usr/include/asm/hw_irq.h:31: error: `NR_IRQS' undeclared here (not in a functio n)
sundance_main.c: En la función `netdev_open':
sundance_main.c:873: aviso: al pasar el argumento 2 de `request_irq' de tipo de puntero incompatible
make: *** [sundance_main.o] Error 1

i dont know why and i dont know what its going on. The adapter is a Advantek Networks ALN-101C and of course it works good under XP. Sorry about my english im from latin america :P  

thanks in advance

---

