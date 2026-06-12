---
title: "Spotify in terminal"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Trandre on 2011-01-07
Trying to run the following, what am i doing wrong?

[HTML]So how do you get it? We’ve packaged it for Debian Squeeze/Ubuntu 10.04 package and for Fedora 13, i386 and x86_64.

Debian
# 1. Add this line to your list of repositories by 
#    editing your /etc/apt/sources.list
deb http://repository.spotify.com stable non-free

# 2. Run apt-get update
# 3. (optional) If you want to verify the downloaded packages,
#    you will need to add our public key

gpg --keyserver wwwkeys.de.pgp.net --recv-keys 4E9CFF4E
gpg --export 4E9CFF4E |sudo apt-key add -

# 4. Run apt-get install spotify-client-qt spotify-client-gnome-support[/HTML]

[HTML]
(through google translate)
W: Failed to obtain http://repository.spotify.com/dists/stable/Release Unable to find entry non-fre/binary-amd64/Packages Expected in Meta-index file (Malformed Release file?)

E: Could not download all the index files. They were ignored, or old ones used instead.

original text:
W: Klarte ikke å skaffe http://repository.spotify.com/dists/stable/Release  Unable to find expected entry  non-fre/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Klarte ikke å laste ned alle oversiktfilene. De ble ignorerte, eller gamle ble brukt isteden. 
[/HTML]


source:[http://www.spotify.com/no/download/previews/](http://www.spotify.com/no/download/previews/)

---

### Post by omeomi on 2011-01-07
"Unable to find entry **non-fre**/binary-amd64/Packages"

Perhaps you misspelled 'non-free' in your sources.list ?

---

### Post by Trandre on 2011-01-09
A bit embarrassing, It was misspelled, thanks

---

