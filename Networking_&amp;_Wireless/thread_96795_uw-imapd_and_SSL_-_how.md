---
title: "uw-imapd and SSL - how?"
date: 2005-11-29
forum: Networking &amp; Wireless
---

### Post by pestie on 2005-11-29
I posted this earlier in the general Ubuntu forum, but it got no replies, so maybe it was in the wrong place.

I just loaded my web/mail server with Ubuntu, and for the most part it's great. However (ever notice how there's always a "however"?), I can't for the life of me get uw-imapd to work with SSL. If I use something like netcat to talk directly to port 993, I can see quite plainly that it's not talking SSL at all - it just answers in plaintext.

I just want a secure IMAP server. Thunderbird doesn't support STARTTLS, so that's out. I don't want to use Maildir, so Cyrus IMAPD is out. That leaves uw-imapd and maybe dovecot, but I know nothing about dovecot. If there's a way to make uw-imapd work, I'd love to hear about it. If dovecot will work, I'll use that. I'm getting a little desperate here, 'cause reading my mail spool with "less" kinda sucks. :smile: 

Thanks in advance for any and all replies.

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=pestie]I posted this earlier in the general Ubuntu forum, but it got no replies, so maybe it was in the wrong place.

I just loaded my web/mail server with Ubuntu, and for the most part it's great. However (ever notice how there's always a "however"?), I can't for the life of me get uw-imapd to work with SSL. If I use something like netcat to talk directly to port 993, I can see quite plainly that it's not talking SSL at all - it just answers in plaintext.

I just want a secure IMAP server. Thunderbird doesn't support STARTTLS, so that's out. I don't want to use Maildir, so Cyrus IMAPD is out. That leaves uw-imapd and maybe dovecot, but I know nothing about dovecot. If there's a way to make uw-imapd work, I'd love to hear about it. If dovecot will work, I'll use that. I'm getting a little desperate here, 'cause reading my mail spool with "less" kinda sucks. :smile: 

Thanks in advance for any and all replies.[/QUOTE]

Would something like stunnel help?
[http://www.stunnel.org/]("http://www.stunnel.org/")

---

### Post by mechanic on 2005-11-30
I've just been trying to do a similar task, simply to allow one machine to act as a central repository of mailboxes with others allowed to use them from local clients (Pine in my case - works well on Linux and on Windows). The Pine client is designed round IMAP so expects an IMAP server on the machine with the mailboxes. The UW imapd looked a good bet because UW (University of Washington) are the developers of Pine. Installing and running imapd didn't get me very far, it was clear from other posts and web-pages that I needed inetd to be running in order to manage imapd (don't you just love Linux!).

The Ubuntu repositories list more than one version of inetd (and none are installed by default), but one with the friendly U. logo next to it in Synaptic (netkit-inetd) looked appropriate so I installed that. 

The impapd generates a local certificate so the SSL side of things is taken care of. (According to the UW site it's buit-in). The last thing to do was to enter a line in inetd.conf to link in the imap daemon:

imap    stream  tcp     nowait  root    /usr/etc/imapd imapd

Then test with "telnet 127.0.0 1 143" on the machine running inetd (it has to be manually started at this stage).

So then I could log onto this machine from another on the LAN and read the maiboxes in (say) PC-Pine. Some minor grumbling from the connection about non-validated certificates, but that's easily brushed aside.

Next for me is to set up regular downloads from the ISP's POP server, and to link POPFile in to combat spam.

I don't suppose all that helps too much, but as I was going through some of the same torment, I thought I'd share!

m.

---

### Post by pestie on 2005-11-30
**cwaldbieser**: I actually considered stunnel, as I'd worked with it a fair amount a few years back. The problem is, however, that the UW IMAP server refuses to allow plaintext password logins unless you're using its built-in SSL support. Stunnel simply listens on (in this example) port 993 and creates a loopback connection to port 143, so as far as the IMAP server can tell, you're not using SSL. All this would be a moot point if Thunderbird supported STARTTLS, but it doesn't. :( 

Well, I finally came up with a solution - I installed [Dovecot](http://www.dovecot.org/). It's in the repositories, it's easy to set up, it's small and lightweight, it doesn't need inetd/xinetd, and so far it works perfectly. The one thing that makes me nervous about it is that the version in the repositories supports MySQL, which means it also installs the MySQL client libraries as a dependency. I run a MySQL 5 server on the same machine I use for e-mail, so now I have MySQL 5.0.16 and MySQL 4 client libraries on the same box. I just have to be careful about hand-compiling things in the future to make sure any configure scripts find the correct client libraries. But since I hand-installed MySQL 5 to /usr/local and didn't add any "lib" directories to /etc/ld.so.conf or the path, I think I should be fine.

Anyway, if anyone else runs into frustrations with UW's IMAP server, scrap it and try Dovecot. It works beautifully.

---

