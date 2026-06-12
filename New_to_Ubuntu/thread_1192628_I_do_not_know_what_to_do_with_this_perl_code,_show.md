---
title: "I do not know what to do with this perl code, show me how to use it"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by marklodge on 2009-06-20
I'm trying to follow this: [http://wiki.squid-cache.org/Features/StoreUrlRewrite](http://wiki.squid-cache.org/Features/StoreUrlRewrite)

Where i am stuck is:[COLOR=DarkRed]
[/COLOR]> 
[COLOR=DarkRed]Then you need a helper. Here's what I've been using: [/COLOR]


```


[COLOR=Black]$| = 1;

while (<>) {
        chomp;
        # print STDERR $_ . "\n";
        if (m/kh(.*?)\.google\.com(.*?)\/(.*?) /) {
                print "http://keyhole-srv.google.com" . $2 . ".SQUIDINTERNAL/" . $3 . "\n";
                # print STDERR "KEYHOLE\n";
        } elsif (m/mt(.*?)\.google\.com(.*?)\/(.*?) /) {
                print "http://map-srv.google.com" . $2 . ".SQUIDINTERNAL/" . $3 . "\n";
                # print STDERR "MAPSRV\n";
        } elsif (m/^http:\/\/([A-Za-z]*?)-(.*?)\.(.*)\.youtube\.com\/get_video\?video_id=(.*) /) {
                # http://lax-v290.lax.youtube.com/get_video?video_id=jqx1ZmzX0k0
                print "http://video-srv.youtube.com.SQUIDINTERNAL/get_video?video_id=" . $4 . "\n";
        } else {
                print $_ . "\n";
        }
}[/COLOR]
```I do not know what to do with this code
Do i compile it? if so, how?
I'm running Debian.

They just say:* configure a rewriter helper* with this script.

---

### Post by MontelEdwards on 2009-07-14
1. you dont compile perl code
2. if you're asking this you dont need to use it:)

---

