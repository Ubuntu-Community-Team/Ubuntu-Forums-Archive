---
title: "Ubuntu on VM..What are the Drawbacks?"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by edarcko on 2010-02-08
Hello,

What are the drawbacks for using ubuntu on a VM on windows7. I want to know everything because i am going to use it for security practice given i study security, and for software development mostly android.

thanks.

---

### Post by ggaaron on 2010-02-08
It will be slower than a native install, you might get noticeable longer compilation times of your software. Also graphics acceleration will probably be slow - high quality movies/opengl applications might not work well.

---

### Post by edarcko on 2010-02-08
hey...so what you are saying is..its all about performance issue rather than not being able to use security networking tools, or compiling codes.

---

### Post by shriramrs31 on 2010-02-08
I agree with ggaaron's reply. For normal use, its mostly about performance - CPU wise and Graphics capability wise. If you have a system that supports V-TX (intel) or SVM(AMD), the performance will be much better.

But there is a possibility that, in case you are using some specific functionality of a processor (just a hypothesis, don't know if there is something like that) that offers a hardware security feature or something like that, you might not be able to use it, because your installation on virtual machine is over an emulated hardware. This applies to also special security chips that might come along with your system.

You can create your own customised ubuntu on an usb-stick or installing with a dual-boot option is not complicated at all.

I run a Xubuntu installation using virtual box, in one of my windows PCs for development purpose and am totally satisfied with it ;-) The seamless mode in virtual box makes the experience even more smoother.

---

### Post by ggaaron on 2010-02-08
> **edarcko said:**
> hey...so what you are saying is..its all about performance issue rather than not being able to use security networking tools, or compiling codes.

You can use whatever tools you want - your only restriction will be the emulated hardware as shriramrs31 said but that shouldn't be a problem. And about developing software in a VM - I've done that too, no problems with it.

---

