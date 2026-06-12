---
title: "Cannot download wi-fi adapter driver in 20.04"
date: 2020-09-09
forum: Networking &amp; Wireless
---

### Post by sootysoot on 2020-09-09
I purchased this Cudy WU-1300 Wi-Fi Adapter: [https://smile.amazon.com/gp/product/B07XXQTW27/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1](https://smile.amazon.com/gp/product/B07XXQTW27/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

I tried using the CD it came with to download the driver, but nothing happened automatically and any of the files I tried to run did nothing or had an error. I also tried downloading the driver (via USB from another computer since I have no internet on my new PC) and the same thing happened. The Cudy website's manual has download instructions for 18.04/19.10. Is there something I can do to make this work on 20.04? Thank you for any help.

---

### Post by morrownr on 2020-09-09
It appears your device is the Cudy WU1300. Downloading the driver from the Cudy site shows the driver to be the driver for the rtl88x2bu. That likely means your chipset is a rtl8812bu.  While the driver on the Cudy website may work, a better and much more up to date solution that is tested with Ubuntu 20.04 can be found here:

 [https://github.com/morrownr/88x2bu](https://github.com/morrownr/88x2bu)

Please follow the instructions for DKMS installation and me know if the instructions are unclear or you have a problem.

Please give us a report on this device. I'm looking for something like this.

---

### Post by SeijiSensei on 2020-09-09
I suggest first using the Driver Manager in Ubuntu and seeing whether it can install the correct driver.

---

