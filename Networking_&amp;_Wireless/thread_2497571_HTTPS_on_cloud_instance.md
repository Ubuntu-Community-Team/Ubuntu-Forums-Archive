---
title: "HTTPS on cloud instance"
date: 2024-05-10
forum: Networking &amp; Wireless
---

### Post by lithsmith on 2024-05-10
I'm playing with a little cloud server running ubuntu.

The apps included in the control panel options are all https enabled all ready to go at the click of a button.

But, I want a Navidrome server.

Docker is disabled in the container/vm whatever, the navidrome binary works great and I have it up, running and playing tunes on my stereo at the moment.

The issue is no https and I'm a little lost at this stuff, nginx seems popular but I think is docker only.

I've been prodding at caddy but not really sure what I am doing. standard ports are not an option, but I have a few ports to play with 

Is there a simple way to get https set up for stuff that's not just 'click to deploy; from the vendor admin panel?

---

### Post by currentshaft on 2024-05-10
gh

---

### Post by TheFu on 2024-05-10
> **lithsmith said:**
> I'm playing with a little cloud server running ubuntu.

Great!  This can be fun.

> **lithsmith said:**
> The apps included in the control panel options are all https enabled all ready to go at the click of a button.
I've never used a control panel on a VPS after the OS install.  From that point on, it is most common to remotely manage via ssh.  If you aren't using ssh, you are doing it wrong.

> **lithsmith said:**
> But, I want a Navidrome server.
Never heard of  Navidrome.  Sounds like someone is good a marketing. You don't need it and may not want it.  That judgement is up to you, but every layer your control is away from the real daemons, the more likely it is to fail and you don't be able to fix it.

> **lithsmith said:**
> Docker is disabled in the container/vm whatever, the navidrome binary works great and I have it up, running and playing tunes on my stereo at the moment.

Uh ... ok.  You've lost me here. Why would you want to stream music from a remote server rather than inside your LAN?  A Raspberry pi v2 can easily provide a music server for you house.  There are lots of techniques. I use MPD with an mpd client to control it, but there must be 50+ other ways - well there are thousands of other ways if you want to get your hands dirty with scripts.

> **lithsmith said:**
> The issue is no https and I'm a little lost at this stuff, nginx seems popular but I think is docker only.
HTTPS is for privacy, not security.  People make that mistake all the time. I see so many How-To guides that claim adding HTTPS is "securing a server".  It is not.  Watch this security conference talk to understand what SSL/TLS is and is not.  [https://www.youtube.com/watch?v=eRWbNno4sN4](https://www.youtube.com/watch?v=eRWbNno4sN4)  You'll learn much, but it isn't hard. It is just clearly explained.

> **lithsmith said:**
> I've been prodding at caddy but not really sure what I am doing. standard ports are not an option, but I have a few ports to play with 
I take it that caddy is some sort of proxy software?  I use nginx for all TLS termination and HA-Proxy for non-TLS routing on a few systems.  Just depends what you need/want.  You can do forwarding using a router or the firewall too.  Lots of techniques, but only you know what you want, so only you can decide which is the best answer.

> **lithsmith said:**
> Is there a simple way to get https set up for stuff that's not just 'click to deploy; from the vendor admin panel?

That would 100% depend on the admin panel.  I've never used on in that way, since installing TLS certs are really easy for both paid 3-5 yr certs or free 90 day certs from let's encrypt.  Just depends on what you want.

Until you know what you want, nobody can help.  I've tried to outline some possibilities for your consideration.  Lots of details are important in making a choice.

If you want real security, use a full VPN or ssh with ssh-keys/-certs.  I run a VPN server at home, so I can have access to my LAN from anywhere in the world just like I were at home.  I also have an ssh port open, since ssh can be used as a SOCKS proxy to access LAN websites from anywhere too.  ssh as a socks proxy is convenient for my linux laptop, but not so much for phones or tablets. That's where the VPN works better.

Beware that there's an old attack that just became published in the last 2 weeks for running any VPN client on MS-Windows. Linux isn't impacted.  Seems a Windows client leaks all sorts of information and can have the VPN completely redirected through a different server by the attacker.  Think it is related to DHCP options on MS-Windows that cannot be disabled.

---

### Post by lithsmith on 2024-05-10
> **currentshaft said:**
> If you're just setting this up for yourself, you really don't need HTTPS. Just tunnel whatever protocol you want over SSH which is encrypted end-to-end and secure.

If you want others to access it, best way to do so is a Let's Encrypt cert using something like ACME, and use nginx/lighttpd/apache to create a virtual host for your application.

It's not just for me.

nginx seems the go to, but the options are all docker based I've seen and docker doesn't work in the cloud instance. I've was trying caddy as that looks like it can do the job but will check lighttpd & apache, thanks

---

### Post by TheFu on 2024-05-10
> **lithsmith said:**
> It's not just for me.

nginx seems the go to, but the options are all docker based I've seen and docker doesn't work in the cloud instance. I've was trying caddy as that looks like it can do the job but will check lighttpd & apache, thanks

I don't use docker (so many reasons for this), but I use **nginx** as a reverse proxy for about 20 domains.  Some run in lxc containers, but many run inside VMs.  My reverse proxy machine also runs a few static websites or simple cgi-based websites on it.

Apache is the "everything you can imaging" web server.  That makes it complicated. More complex means more code. More code means more chances for coding errors, some will be serious.  Nginx has become the "almost-everything" web server. 20 yrs ago, it was small, fast.  As it matured, more and more "features" were added for good reason.

HA-Proxy is much easier for people just starting.  There must be 20 other slightly popular proxy servers.  I've used a few over the decades.  Each was relatively easy to setup, but harder to maintain. HA-Proxy is in the Canonical repos, so it should be maintained and patched as needed.  That's a good thing.

This may be interesting to you.  [https://www.loggly.com/blog/benchmarking-5-popular-load-balancers-nginx-haproxy-envoy-traefik-and-alb/](https://www.loggly.com/blog/benchmarking-5-popular-load-balancers-nginx-haproxy-envoy-traefik-and-alb/)  Under load, HAProxy performs better than nginx, which is better than the other 3 reverse proxy tools they looked at.   I use HAProxy mainly to forward some non-Web traffic unmolested from a public VPS down a VPN tunnel to a server under my completely control.  The VPN connection starts from inside my LAN, so if my LAN public IP changes, this doesn't impact service.  Externally, the same VPS public IP is used.

---

### Post by lithsmith on 2024-05-10
> **TheFu said:**
> Great!  This can be fun.


I've never used a control panel on a VPS after the OS install.  From that point on, it is most common to remotely manage via ssh.  If you aren't using ssh, you are doing it wrong.


Never heard of  Navidrome.  Sounds like someone is good a marketing. You don't need it and may not want it.  That judgement is up to you, but every layer your control is away from the real daemons, the more likely it is to fail and you don't be able to fix it.



Uh ... ok.  You've lost me here. Why would you want to stream music from a remote server rather than inside your LAN?  A Raspberry pi v2 can easily provide a music server for you house.  There are lots of techniques. I use MPD with an mpd client to control it, but there must be 50+ other ways - well there are thousands of other ways if you want to get your hands dirty with scripts.


HTTPS is for privacy, not security.  People make that mistake all the time. I see so many How-To guides that claim adding HTTPS is "securing a server".  It is not.  Watch this security conference talk to understand what SSL/TLS is and is not.  [https://www.youtube.com/watch?v=eRWbNno4sN4](https://www.youtube.com/watch?v=eRWbNno4sN4)  You'll learn much, but it isn't hard. It is just clearly explained.


I take it that caddy is some sort of proxy software?  I use nginx for all TLS termination and HA-Proxy for non-TLS routing on a few systems.  Just depends what you need/want.  You can do forwarding using a router or the firewall too.  Lots of techniques, but only you know what you want, so only you can decide which is the best answer.



That would 100% depend on the admin panel.  I've never used on in that way, since installing TLS certs are really easy for both paid 3-5 yr certs or free 90 day certs from let's encrypt.  Just depends on what you want.

Until you know what you want, nobody can help.  I've tried to outline some possibilities for your consideration.  Lots of details are important in making a choice.

If you want real security, use a full VPN or ssh with ssh-keys/-certs.  I run a VPN server at home, so I can have access to my LAN from anywhere in the world just like I were at home.  I also have an ssh port open, since ssh can be used as a SOCKS proxy to access LAN websites from anywhere too.  ssh as a socks proxy is convenient for my linux laptop, but not so much for phones or tablets. That's where the VPN works better.

Beware that there's an old attack that just became published in the last 2 weeks for running any VPN client on MS-Windows. Linux isn't impacted.  Seems a Windows client leaks all sorts of information and can have the VPN completely redirected through a different server by the attacker.  Think it is related to DHCP options on MS-Windows that cannot be disabled.

I live on ssh, it's the first thing I enabled and my preference, but it's a cheap instance and is more aimed at clicking on an admin panel, docker for example is disabled, chroots and qemu seem problematic, I've got Gentoo Prefix up and running though, which is nice to have around. As an example they offer an app to transcode media files in the control panel that is disabled unless you pay for a better subsciption, but ssh+ffpmeg will transcode all day long just fine in the cheap seats which suits me just fine.

I'm cheating with the daeoms at the moment, the system uses s6 which I don't know too well so just have tmux/crontab kinda stuff whislt I sort things out, I don't have any reason to be wary of navidrome as a service or s6 as manager, I've relied on them both heavily, they don't let me down and will set them up properly one I'm comfortable with the other bits.

I may not 'need' Navidrome but I've used it the past year or on my pi and it's the best bit of software I've used in a very long time, total game changer. It's solid, I love it. It's the reason I want a cloud service. I have zero interest in going back to mpd, ditched that many years ago, I do have mopidy for UPnP on my rpi4>dac>amp and could switch it for mpd, but mopidy does the job just fine. Server is in the cloud, connects to my phone, I use that to cast to UPnP via modpiy on the rpi for the main stereo. I have all of my music on all devices available everywhere in whatever format I want and friends are happy too.

I've been selfhosting Navidrome from my rpi4 for a year or so. I have a tailscale for api access for me, and a tailscale funnel for a few friends using it via the webUI. It's not ideal. They have limited access, no API :(, and a few transcode jobs at the same time will swamp the pi, I use it as a local Kodi box and I can't watch a movie in peace if my android app queues up a few hundred tunes to transcode or a few people are transcoding albums at the same time. I'm also using spinning rust for media storage via usb docks which are slow and not exactly silent and my uploads speeds are grim. The cloud instance is far superior for performance across the board and I don't need to lie at night listening to spinning rust struggling to transcode 3000 tunes as I wanna try 256 OPUS for lolz this week and the service is stuttering for friends on the other side of the world. I would like to expand to a full hetzner server auction system one day, but this feels like plenty power just now and good training wheels for pennies.

I also like to try a lot of stuff on my pi, it's my tiny homelab, I like to be able to reboot, switch out disk, try new things, break things, fix things, test things etc. and I'd prefer my music was more like running water from the council. If for a few quid a month I can have a superfast bulletproof cloud server with navidrome, slsk, and beets somewhat automated that runs 24/7 and everyone can hammer it as much as they want and add to it, that would be nice.

I'd don't need anything super secure, it's just mainly music that I have backed up locally, but if it involves other users, passwords and admins, https seems sensible to me. The https stuff is new to me, maybe I just need letsencrypt and not nginx/lighttpd/apache/caddy?

If you are using mpd, I'd give navidrome a spin. mpd + yaste or whatever was kinda tolerable for me on a pi1 a decade ago but after a few years of gripes and mediocre apps I just went to mpv+ranger+ssh, then jellyfin and finally am delighted with navidrome, the subsonic ecosystem is pretty well supported.

---

### Post by lithsmith on 2024-05-10
Thanks, will try out HA-Proxy shortly, I don't think load is gonna be a big issue at the moment....but if it's simple to setup and performs well that sounds good to me, if I add jellyfin for video the load might jump somewhat.

---

### Post by TheFu on 2024-05-10
> **lithsmith said:**
> Thanks, will try out HA-Proxy shortly, I don't think load is gonna be a big issue at the moment....but if it's simple to setup and performs well that sounds good to me, if I add jellyfin for video the load might jump somewhat.

No way would I place jellyfin directly on the internet.  Behind a VPN, fine. Behind an ssh-socks proxy, fine.  Never on the internet.

Jellyfin is too complex and has the DotNet bloat.  I'm willing to use it on my LAN, but no way would I trust it to be secure enough for direct access over the internet.  Same goes for Nextcloud.  I use both, BTW.

Perhaps we have different risk tolerance levels?

---

### Post by TheFu on 2024-05-10
> **lithsmith said:**
> I live on ssh, it's the first thing I enabled and my preference, but it's a cheap instance and is more aimed at clicking on an admin panel, docker for example is disabled, chroots and qemu seem problematic, I've got Gentoo Prefix up and running though, which is nice to have around. As an example they offer an app to transcode media files in the control panel that is disabled unless you pay for a better subsciption, but ssh+ffpmeg will transcode all day long just fine in the cheap seats which suits me just fine.

I'm cheating with the daeoms at the moment, the system uses s6 which I don't know too well so just have tmux/crontab kinda stuff whislt I sort things out, I don't have any reason to be wary of navidrome as a service or s6 as manager, I've relied on them both heavily, they don't let me down and will set them up properly one I'm comfortable with the other bits.

I may not 'need' Navidrome but I've used it the past year or on my pi and it's the best bit of software I've used in a very long time, total game changer. It's solid, I love it. It's the reason I want a cloud service. I have zero interest in going back to mpd, ditched that many years ago, I do have mopidy for UPnP on my rpi4>dac>amp and could switch it for mpd, but mopidy does the job just fine. Server is in the cloud, connects to my phone, I use that to cast to UPnP via modpiy on the rpi for the main stereo. I have all of my music on all devices available everywhere in whatever format I want and friends are happy too.

I've been selfhosting Navidrome from my rpi4 for a year or so. I have a tailscale for api access for me, and a tailscale funnel for a few friends using it via the webUI. It's not ideal. They have limited access, no API :(, and a few transcode jobs at the same time will swamp the pi, I use it as a local Kodi box and I can't watch a movie in peace if my android app queues up a few hundred tunes to transcode or a few people are transcoding albums at the same time. I'm also using spinning rust for media storage via usb docks which are slow and not exactly silent and my uploads speeds are grim. The cloud instance is far superior for performance across the board and I don't need to lie at night listening to spinning rust struggling to transcode 3000 tunes as I wanna try 256 OPUS for lolz this week and the service is stuttering for friends on the other side of the world. I would like to expand to a full hetzner server auction system one day, but this feels like plenty power just now and good training wheels for pennies.

I also like to try a lot of stuff on my pi, it's my tiny homelab, I like to be able to reboot, switch out disk, try new things, break things, fix things, test things etc. and I'd prefer my music was more like running water from the council. If for a few quid a month I can have a superfast bulletproof cloud server with navidrome, slsk, and beets somewhat automated that runs 24/7 and everyone can hammer it as much as they want and add to it, that would be nice.

I'd don't need anything super secure, it's just mainly music that I have backed up locally, but if it involves other users, passwords and admins, https seems sensible to me. The https stuff is new to me, maybe I just need letsencrypt and not nginx/lighttpd/apache/caddy?

If you are using mpd, I'd give navidrome a spin. mpd + yaste or whatever was kinda tolerable for me on a pi1 a decade ago but after a few years of gripes and mediocre apps I just went to mpv+ranger+ssh, then jellyfin and finally am delighted with navidrome, the subsonic ecosystem is pretty well supported.

For fast transcoding, I have the Ryzen iGPU doing it.  h.264 or h.265 - both take the same time. The CPU is barely touched.  Jellyfin can trancode on the fly if you configure it.  My Pi4 hates VP9.  It stutters, locks up, and worse.  I transcode on the fly all VP9 to h.265 (which seems unnecessary) and that works well.  On my Pi3, I transcode to h.264.

I don't transcode anything on r-pi systems.  They are playback only devices here.  Both run Kodi with the Jellyfin client. Usually controlled from a tablet, but also from a RC6 remote.

HTTPS **is** the minimal requirement for internet privacy, but don't consider it security.

I've been using mpd for 5+ yrs and it meets my needs.  I don't change unless there's a good reason.  I also have a script that uses mpv with playlists with a grep to find the playlist.  I don't stream music to my phone when outside the home.  About every 6 months, I'll copy a new set of audio files.  I don't care about sharing copyrighted files with others. Not something I do.

Opus is dead. Use **vorbis** for audio.  I can't hear the difference between FLAC and 192 Kbps vorbis/ogg.  I've tried using my Shure earplugs. Can't hear the difference.  Guess that happens when you get old like me.

---

### Post by lithsmith on 2024-05-10
Jellyfin was just a thought regarding the other poster mentioning load.

I was under the impression it was the other way around, opus is the future, ogg is old tech and xiph were moving away from in favour of opus as offers excellent performance across the board. Perhaps I am confused.

I archive in flac, I often transcode, I can tell a difference at 192ogg on my main rig, 256 gets tough, but I visit friends with some really nice rigs and it's nice to have the good stuff at the touch of a button. Or at the beach with mum, a bluetooth speaker and one bar reception and can grab the song she's talking about from dad's old meatloaf cd I've ripped and not listened to for a decade in 64kbps.

We may have different ideas about security, my personal data at home I don't expose without care, a cloud navidrome server or funkwhale pod is pretty much disposable if anything goes wrong in my current thinking and if someone exposes my beefeart collection or scrobbler stats on the darkweb, I'll cope and hopefully learn a lesson. I'm trying to implement [exactly what they suggest]("https://www.navidrome.org/docs/usage/security/#network-configuration"), but just new to this stuff.

I'm here as I don't wanna expose my home network, for a few quid I wanna play in the cloud, if **** hits the fan, I'll need to rsync my tunes to a fresh instance and rethink security.

If copying files to your phone every few months and using mpd on the local network works for you, fair enough, I found it a pita and am delighted to leave it behind, was fun in 2003 when I got a 20GB ipod classic and ~2010 when I started playing with mpd, but I think there may be a reason almost everyone, and every artist, I know uses streaming services for years now. I do like the old school approach sometimes, but like vinyl for that.


I'm in a tiny studio flat with an rpi4, my laptop and desktop are over a decade old. I don't really want some beefy cpu with fans going in the corner, I got rid of my big black box years back. I may upgrade hardware someday to something tiny, silent, powerful and all round awesome, but I'm in no rush and things aren't getting any cheaper.

---

### Post by lithsmith on 2024-05-10
.

---

### Post by TheFu on 2024-05-10
Don't confuse encoding with the file container.  ogg is a file container. Vorbis is an encoding. Same for opus - it is an encoding.

mka, ogg, mpa, mp3 are file containers.

AAC, mp3 (mpeg2 Layer III), opus, vorbis are all encodings.

My cell plan doesn't have unlimited data.  There's only so much $30/yr buys.  Just a few weeks ago, I got my first cell data plan since around 2017.  I don't travel like I used to and being connected hasn't been an issue.  When I travel, I'll oven get a 1GB / 1 week for $10 in the new country.  A few times, laws in the country have prevented that or in some places there wasn't any cell coverage at all because they were extremely remote.  If I weren't planning so much travel, I wouldn't have gotten a cell data plan.

As for copying files, there are lots of ways.  nextcloud, rsync and if I'm in a hurry, I'll pull the microSD card and use a USB adapter.

I have a 4 bdr house on some land.  Our situations are vastly different.  My computers aren't where we sleep.  Newer computers are quiet.  Fans are quiet. They are fairly powerful and relatively cheap.  It is amazing what $200 can buy if you reuse the case, PSU, monitor, etc.  A single mid-tower easily handles 20TB of storage and 15 VMs.  Actually, my Pi v4 is by far the the noisiest computer in the house.  

Yep, vastly different worlds.

---

### Post by lithsmith on 2024-05-10
Cheers, different strokes for different folks.

I'm not sure how that ties in with opus being dead and vorbis the future. They are both encoders from related teams and opus is the new stuff, far from dead afaiu.

My mobile data use is minimal, even switched off it's a nice setup, it caches over wifi and I'm not often without wifi for long, if I do want a specific song or album on demand I can spend a few megs. My daughter uses the same kinda idea with ytmusic, but they lock everything on her device if the subscription isn't paid.

I will likely pick up a little quiet little server at some point but am in no rush, and the stuff I want always seems a year or two away or just out of budget atm, the cloud seems like a safe place to play and test out some ideas with data I'm not worried about losing or leaking if something goes wrong. I've got a free month to play with this machine, I'm learning a little, pleased with how it all performs and will see how things go.

---

### Post by TheFu on 2024-05-10
Looks like my memory between opus and vorbis is flawed.   Just read that opus is better for short clips.
[https://sound.stackexchange.com/questions/42711/what-is-the-difference-between-vorbis-and-opus](https://sound.stackexchange.com/questions/42711/what-is-the-difference-between-vorbis-and-opus)
> Opus is the successor for Vorbis, created by the same company and applicable to a wider range of audio qualities and rates while having low latency.

_Clearly I was wrong.  Not the first time, even today._

I did lots of research about this a few years ago when I was re-ripping my CD collection. It was originally ripped in the late 1990s and took about an hour per CD at the time.  Now it is 5 minutes per CD.  Anyway, I decided to use Vorbis, not Opus for some reason. I did test Opus.  Perhaps one of my players didn't support it?  IDK.  Perhaps it was an older Android tablet that refused to play it, but handled Vorbis just fine.  Vorbis is supported on all my players and in every modern browser.

---

