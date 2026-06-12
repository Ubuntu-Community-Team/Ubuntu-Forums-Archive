---
title: "how to disable caching video"
date: 2013-11-07
forum: Networking &amp; Wireless
---

### Post by tarzq306 on 2013-11-07
hey guy, can u help me how to disable squid 3.1 to caching video content, i'm using ubuntu 12.04 and using squid 3.1 as my proxy. if you know how to disable it, please help me

---

### Post by SeijiSensei on 2013-11-08
Write an ACL that keys on the video mimetype then uses the "cache" directive to deny caching. See this for a similar example: [http://wiki.squid-cache.org/SquidFaq/SquidAcl#how_do_I_configure_Squid_not_to_cache_a_specific_server.3F](http://wiki.squid-cache.org/SquidFaq/SquidAcl#how_do_I_configure_Squid_not_to_cache_a_specific_server.3F)

Also, this posting has a pretty complete list of video mimetypes: [http://www.linuxquestions.org/questions/linux-software-2/squid-rep_mime_type-or-req_mime_type-807710/](http://www.linuxquestions.org/questions/linux-software-2/squid-rep_mime_type-or-req_mime_type-807710/).  If you put all the types into a file as described there, you should be able to disable caching for all of them like this:

```

acl video_mime rep_mime_type -i "/etc/squid/video_mime_types"
cache deny video_mime

```

---

