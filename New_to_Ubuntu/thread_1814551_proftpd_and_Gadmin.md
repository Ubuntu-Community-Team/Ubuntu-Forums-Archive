---
title: "proftpd and Gadmin"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Sailor-Moon on 2011-07-29
I have installed proftpd and gadmin to create users for ftp.

When trying to activate a user in gadmin, I am getting the following error message
**************************************************************************
 - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 65 of '/etc/proftpd/proftpd.conf'

**************************************************************************

Does anyone know how to fix this please.
Thanks in advance

---

### Post by Sailor-Moon on 2011-07-29
I'm now getting this

 - mod_dso/0.5: module 'mod_ctrls_admin.c' already loaded
 - Fatal: LoadModule: error loading module 'mod_ctrls_admin.c': Operation not permitted on line 6 of '/etc/proftpd/proftpd.conf'

---

### Post by skatinjj on 2011-07-29
Wrong place.......sorry

---

### Post by skatinjj on 2011-07-29
Are you trying this from terminal or GUI?

---

### Post by Sailor-Moon on 2011-07-30
GUI.
Its when I'm in Gadmin and I've created a user who is by default deactivated.
I click the activate button and then get these errors

---

### Post by Sailor-Moon on 2011-07-30
I think I have worked out that proftpd.conf file asks for include /etc/proftpd/modules.cof it gices a path for modules to load /usr/lib/proftpd 1st module to load is mod_ctrls_admin.c but this file is missing from the folder, co it can't load it.

I have found instructions on how to solve this.
This module requires that controls support be enabled in proftpd via the --enable-ctrls configure option. Follow the normal steps for using third-party modules in ProFTPD:

./configure --enable-ctrls --with-modules=mod_ctrls_a&#8203;dmin
make
make install

I am not sure what or where to create type or use ./config  and the rest of the instructions.
Is this just types into a terminal window or is there a file I have to add this code to?  any help would be apprecieated

---

### Post by skatinjj on 2011-07-30
Do you have the link to the instructions you found?  The command is ran from a terminal.

---

### Post by Sailor-Moon on 2011-07-31
I'm afraid I just closed the window seconds before reading your reply.

I have worked around this by un-installing.
Installing WINE and using filezilla server. I know there are limitations, but it works for me. So I will close this thread and thank all who have helped.

---

