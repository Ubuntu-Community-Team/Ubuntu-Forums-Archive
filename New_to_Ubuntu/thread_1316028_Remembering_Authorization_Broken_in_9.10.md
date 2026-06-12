---
title: "Remembering Authorization Broken in 9.10?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by inrig on 2009-11-05
I've just upgraded to 9.10, and I like most of what I've seen so far. However I have encountered one irritant. I occasionally want to mount my Windows XP partition, which I can easily do via "Places". When I do this, I am asked for a password. In 9.04, the password dialog included a "Remember authorization" checkbox, which enabled me to do subsequent mounts without having to enter the password each time. This checkbox is not provided in 9.10. Is there some other way to avoid having to repeatedly enter passwords?

---

### Post by mikewhatever on 2009-11-05
Mount the partition at boot with ntfs-config or by adding it to fstab.
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

By the way, I wouldn't call what you described broken.

---

### Post by inrig on 2009-11-05
> **mikewhatever said:**
> Mount the partition at boot with ntfs-config or by adding it to fstab.
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

By the way, I wouldn't call what you described broken.

Thank you for your quick reply.  I realize that I could permanently mount the partition, but I use it only occasionally so I didn't do that with Jaunty, and don't particularly want to (although I agree it doesn't really hurt to do so).

I called the capability to remember authorizations "broken" because it was provided and working in the previous release, but it is not in the current release.  Things that used to work and don't anymore could be described as "broken", I think. :)

---

### Post by howefield on 2009-11-05
> **inrig said:**
> I realize that I could permanently mount the partition, but I use it only occasionally so I didn't do that with Jaunty, and don't particularly want to

You could try pysdm, install with Synaptic. It has options that I think would keep to your criteria.

> I called the capability to remember authorizations "broken" because it was provided and working in the previous release, but it is not in the current release.  Things that used to work and don't anymore could be described as "broken", I think. :)

"Broken" implies the feature is there but not usable in some way, "missing" describes your predicament. Maybe.. :)

---

### Post by cariboo on 2009-11-05
Disabled is more like it, although it works form me on both Karmic and Lucid. Both are fresh installs.

---

### Post by howefield on 2009-11-06
> **cariboo907 said:**
> Disabled is more like it, although it works form me on both Karmic and Lucid. Both are fresh installs.

That's interesting, how does one enable this feature ?

---

### Post by mc4man on 2009-11-06
Till such time as they include a way, easy to do yourself

```
gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

```

Find this section and replace what's in  blue as shown, just replace, don't mess with formatting 

Orig
```
  <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]auth_admin_keep[/COLOR]</allow_active>
    </defaults>
  </action>

```

edited
```
  <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]yes[/COLOR]</allow_active>
    </defaults>
  </action>
```

more info
[http://ubuntuforums.org/showthread.php?t=1299820](http://ubuntuforums.org/showthread.php?t=1299820)

( i wouldn't change anything else in that particular file or you may get unexpected behavior

---

