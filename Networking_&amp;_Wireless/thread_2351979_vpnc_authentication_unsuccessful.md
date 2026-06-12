---
title: "vpnc authentication unsuccessful"
date: 2017-02-08
forum: Networking &amp; Wireless
---

### Post by lordbah2 on 2017-02-08
I'm trying to connect from Ubuntu 16.04 to a work system ("Global Protect") and getting
vpnc: authentication unsuccessful

I can't find any obvious reason for failure. There are a couple of "unknowns" in the debug output:

unknown ISAKMP_PAYLOAD_VID: 12f5f28c 457168a9 702d9fe2 74cc0100
unknown ISAKMP_PAYLOAD_VID: a9b9b103 4f7e50a2 513b47b1 00bb85a9

but it seems to just blow by them.

I hope I've deleted everything I need to delete ...

[ATTACH]273587[/ATTACH]

---

### Post by lordbah2 on 2017-02-10
There appears to be only one place this could be coming from in the source:

```

    DEBUGTOP(2, printf("S5.6 process xauth set\n"));
    {
        /* The final SET should have just one attribute.  */
        struct isakmp_attribute *a = r->payload->next->u.modecfg.attributes;
        uint16_t set_result = 1;


        if (a == NULL
            || a->type != ISAKMP_XAUTH_06_ATTRIB_STATUS
            || a->af != isakmp_attr_16 || a->next != NULL) {
            reject = ISAKMP_N_INVALID_PAYLOAD_TYPE;
            phase2_fatal(s, "xauth SET message rejected: %s(%d)", reject);
        } else {
            set_result = a->u.attr_16;
        }


        /* ACK the SET.  */
        DEBUGTOP(2, printf("S5.7 send xauth ack\n"));
        r->payload->next->u.modecfg.type = ISAKMP_MODECFG_CFG_ACK;
        sendrecv_phase2(s, r->payload->next, ISAKMP_EXCHANGE_MODECFG_TRANSACTION,
            r->message_id, 1, 0, 0, 0, 0);
        r->payload->next = NULL; /* this part is already free()d by sendrecv_phase2 */
        free_isakmp_packet(r); /* this frees the received set packet (header+hash) */


        if (set_result == 0)
            error(2, 0, "authentication unsuccessful");
    }
    DEBUGTOP(2, printf("S5.8 xauth done\n"));

```

That "S5.8" is never logged. Nor is "xauth SET message rejected". So it seems a->u.attr_16 must be 0, whatever that means. This is in do_phase2_xauth().

---

### Post by lordbah2 on 2017-02-16
Resolution:
Turns out Global Protect isn't something that vpnc works with, but the folks there pointed me at [https://github.com/dlenski/openconnect](https://github.com/dlenski/openconnect). After a little work with the developer, that now does work for me.

---

