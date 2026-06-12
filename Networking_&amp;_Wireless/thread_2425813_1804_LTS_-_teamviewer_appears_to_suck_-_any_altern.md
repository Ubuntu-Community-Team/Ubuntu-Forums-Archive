---
title: "18:04 LTS - teamviewer appears to suck - any alternatives?"
date: 2019-08-30
forum: Networking &amp; Wireless
---

### Post by steve234 on 2019-08-30
Hi all,

I'm aware of the various VLC packages, but tried team viewer (TV14) as it is more user friendly. My experience has been pretty bad. I have tried:

- Viewing lubuntu box on Android phone - works, BUT, can't send key combinations. This is a known issue, and deal breaker for me on i3WM; and
- Viewing Android Phone (Wileyfox Swift 2 - Oreo) on Linux box. Connection just cycles between connected and finished. This also seems to be broken in TV14

Are there any user friendly cross platform packages I can use. All I find on google is various VLC packages, which are OK, but I was after something more user friendly.

---

### Post by TheFu on 2019-08-31
I don't think you mean VLC.

---

### Post by steve234 on 2019-08-31
Solved - if you are on i3 and want multiple desktops etc - use nomachine (!M) and enjoy remote desktop goodness

---

### Post by kurt18947 on 2019-09-01
> **steve234 said:**
> Solved - if you are on i3 and want multiple desktops etc - use nomachine (!M) and enjoy remote desktop goodness

That looks interesting. I could certainly use remote desktop capability over the internet but have been concerned about security. I skimmed over the NoMachine web site but don't see anything about creating a secure tunnel or similar. Is it first necessary to create an SSH connection? or is the NX protocol secure or something?

---

### Post by Skaperen on 2019-09-01
or x2go.  it uses NX v3-updated over ssh.

---

### Post by TheFu on 2019-09-01
+1 for x2go.
All NX protocols use ssh for authentication and tunnels. It is built in.

---

