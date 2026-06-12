---
title: "kernel debugging problem on ubuntu8.10(2.6.27)"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by anuragccsu on 2009-02-27
kernel debug problem
Hi All
i've ubuntu8.10 with kernel 2.6.27 installed in my system.
I've to debug the kernel using kgdb, for that i searched on net and found that kgdb is avaliaible only for 2.6.15 kernel source.
so i downloaded 2.6.15 kernel source and did everything to compile it referring the link:-
[COLOR="Yellow"]http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/[/COLOR]
(i copied the config file from the kernel installed in my machine having kernel 2.6.27)but in the compilatoin it is giving me the error:

include/asm/mpspec_def.h:78: warning: packed attribute ignored for field of type unsigned char[6]
arch/i386/kernel/apic.c: In function smp_apic_timer_interrupt:
arch/i386/kernel/apic.c:1136: [COLOR="Blue"]sorry, unimplemented: inlining failed in call to smp_local_timer_interrupt: function body not available
arch/i386/kernel/apic.c:1205: sorry, unimplemented: called from here
make[1]: *** [arch/i386/kernel/apic.o] Error 1
make: *** [arch/i386/kernel] Error 2[/COLOR]

so how to work around this problem? plz help.


and one more thing is there any version of kgdb available to debug the 2.6.27 kernel?

thanks

---

