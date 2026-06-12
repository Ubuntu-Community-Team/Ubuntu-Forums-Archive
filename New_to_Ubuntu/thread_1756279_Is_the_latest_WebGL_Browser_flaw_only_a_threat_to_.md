---
title: "Is the latest WebGL Browser flaw only a threat to Windows or/&amp; Mac?"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by metalaxesucks on 2011-05-12
I don't know if this is the right place to post this question, but I don't know where else to find knowledgeable Linux people :)

I only use Firefox & sometimes Chrome on Ubuntu 11.04, but according to this article, it says:
"Firefox and Chrome users are told to turn off WebGL after a security firm warns of "inherent" issues with the rendering tool"
[http://www.itpro.co.uk/633409/webgl-flaws-hit-firefox-and-chrome](http://www.itpro.co.uk/633409/webgl-flaws-hit-firefox-and-chrome)

Does this affect Ubuntu users? Maybe I should use Opera for now?

---

### Post by Vaphell on 2011-05-12
i think it affects all browsers that support WebGL on all platforms. WebGL apparently talks to the driver directly and it's obviously a bad idea to let some random stuff from the web to run directly on your hardware with no sanity checks.

---

### Post by jtarin on 2011-05-12
I've disabled mine on all browsers and I'm not the paranoid type.

---

### Post by donato roque on 2011-05-12
US CERT issued a recommendation to disable WebGL in browsers for now. 

In Firefox, you should go to About:Config. Look for:

Webgl_disable >> true

---

### Post by metalaxesucks on 2011-05-13
I found out that WebGL is not enabled in either FF or Chrome on my Ubuntu Computer.
I just went to this test site
[http://get.webgl.org/](http://get.webgl.org/)
And it gives me the error message:
"Hmm. While your browser seems to support WebGL, it is disabled or unavailable. If possible, please ensure that you are running the latest drivers for your video card."

So I'm not going to worry about it.
Thanks for your input anyways.

---

