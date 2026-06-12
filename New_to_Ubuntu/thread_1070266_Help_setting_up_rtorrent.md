---
title: "Help setting up rtorrent"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by jonw860 on 2009-02-15
I have a server running rtorrent and I am wondering how you would set it to automaticaly add torrents to /home/admin/torrents

---

### Post by m_duck on 2009-02-15
Have a read through [this](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/). I think it's mentioned - I can't remember how much detail though, I don't use it myself.

---

### Post by adult swim on 2009-02-15
you want the downloaded torrents to go there, or do you want it to watch that folder for torrent files to start downloading?

---

### Post by jonw860 on 2009-02-15
Well I would like the torrents to save in say a folder like /home/admin/media or something like that but I want it to watch /home/admin/torrents  .The problem is my rtorrent config file is missing I tried reinstalling it but it didn't install one so I am having to make one from scratch and yea this is all I have to help.
[http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest)

Also if its any help my server has a 100mb connection so what would be the recommended settings for rtorrent?

---

### Post by m_duck on 2009-02-15
[COLOR=Black]The sample configuration file is at [/COLOR] [COLOR=Black]cp /usr/share/doc/rtorrent/examples/rtorrent.rc (mentioned in site above).

To copy it to your home directory:[/COLOR]```
 cp /usr/share/doc/rtorrent/examples/rtorrent.rc ~/.rtorrent.rc
```

I'm not sure about good values to use in the configuration though as I rarely use torrents.

---

### Post by adult swim on 2009-02-15
to save files in /home/admin/media and watch for torrent files in /home/admin/torrents, youd want to save this as ~/.rtorrent.rc ```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
#max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
#upload_rate = 0

# Default directory to save the downloaded torrents.
directory = /home/admin/media

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
#session = ./session

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/admin/torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
#port_range = 6890-6999

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
#use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
# encryption = allow_incoming,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
# 
# dht = auto

# UDP port to use for DHT. 
# 
# dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
# peer_exchange = yes

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10

```  for it to work right, youve got to make sure that the .torrent file ends up in /home/admin/torrents

---

### Post by jonw860 on 2009-02-15
Thanks so much man, is there any changes needed to optimize it for a 100mb connection or will this one work just fine?

---

### Post by jonw860 on 2009-02-15
Oh yea one more thing I can only get on my server over ssh, how do I close out ssh without it shutting rtorrent off?

---

### Post by adult swim on 2009-02-15
check out this thread
[http://ubuntuforums.org/showthread.php?t=817712](http://ubuntuforums.org/showthread.php?t=817712)

---

