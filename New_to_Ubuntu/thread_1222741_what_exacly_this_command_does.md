---
title: "what exacly this command does?"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-25
sudo iptables -L -n -v

---

### Post by SuperSonic4 on 2009-07-25
You can find out by running ```
man iptables
``` and looking up -L -n -v.

sudo means run as root
-v probably means verbose

---

### Post by AsusEEEPC on 2009-07-25
Just type 

```
 whatis iptables 
```

---

### Post by halitech on 2009-07-25
```
 -L, --list [chain]
              List  all rules in the selected chain.  If no chain is selected,
              all chains are listed. Like every  other  iptables  command,  it
              applies  to  the specified table (filter is the default), so NAT
              rules get listed by
               iptables -t nat -n -L
              Please note that it is often used with the -n option,  in  order
              to  avoid  long reverse DNS lookups.  It is legal to specify the
              -Z (zero) option as well, in which case  the  chain(s)  will  be
              atomically  listed  and zeroed.  The exact output is affected by
              the other arguments given.

```
```
 -v, --verbose
              Verbose output.  This option makes the  list  command  show  the
              interface  name,  the  rule options (if any), and the TOS masks.
              The packet and byte counters are also listed,  with  the  suffix
              &#8217;K&#8217;,  &#8217;M&#8217; or &#8217;G&#8217; for 1000, 1,000,000 and 1,000,000,000 multipli&#8208;
              ers respectively (but see the -x  flag  to  change  this).   For
              appending,  insertion,  deletion  and  replacement,  this causes
              detailed information on the rule or rules to be printed.

       -n, --numeric
              Numeric output.  IP addresses and port numbers will  be  printed
              in  numeric format.  By default, the program will try to display
              them as host names, network names, or services (whenever  appli&#8208;
              cable).

```

---

### Post by heyyy on 2009-07-25
thank you all

---

