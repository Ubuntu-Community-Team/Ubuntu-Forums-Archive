---
title: "restart and shutdown messed up"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by c0d4041292 on 2009-05-20
i have a dell inspiron 1720 laptop and when I try to shutdown or restart it makes it through the boot down process but then after the ubuntu screen goes away it goes to a black screen with a white blinking "_"  haha....kinda looks like a smiley... anyways, couldn't really find any post like this but i am in a hurry and didnt do much searching....

---

### Post by Happy_Man on 2009-05-20
Something's not communicating with the BIOs properly. 

More simply, Ubuntu's stopped running, it just failed to tell the BIOs to shut off the computer. Do remember that an OS is simply an application that runs on top of the BIOS, which does the real work in keeping a computer active during the shutdown/startup phases. 

Therefore, you should be fine if you just hold down the power button to actually shut the computer off once it gets there, as there will be no data loss or potential danger.

---

