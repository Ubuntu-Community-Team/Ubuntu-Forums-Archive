---
title: "Huawai cellphone (NOT e220)"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by samden on 2008-08-20
I am trying to connect to the internet (ideally through 3G but GPRS would do) using a Huawei cellphone from Vodafone NZ. This is NOT a the Huawei e220 modem that is becoming rather popular, but a standard 3G cellphone.
[http://www.vodafone.co.nz/help/device-support/vodafone/715/]("http://www.vodafone.co.nz/help/device-support/vodafone/715/")

I have installed the vodafone-mobile-connect-card-driver-for-linux in the hope that it would function like the e220 modem, but this driver cannot detect it automatically. There are options for "Data port device" and "Control port device" for manual configuration but I do not know what to enter there.

I have also tried installing synchronisation software (such as Phone Manager 0.40) to see if this will detect it, and none seem to find the phone.

When I plug the cellphone in to the computer (USB), it must be detected as lsusb returns:
```
Bus 004 Device 006: ID 12d1:1009 Huawei Technologies Co., Ltd.
```

However I can't seem to do anything with it. 

sudo wvdialconf
```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>
```

I have installed setserial but cannot figure out how to use it (yes I have read the man pages!).

How would I assign the cellphone to a port as a modem, I presume using setserial?

If this is the wrong way to go about sorting it out, how else should I do it?

---

### Post by samden on 2008-08-24
I see this is a known bug. This phone will work through bluetooth, at least for file sharing. I am now trying to connect through bluetooth for synchronisation and internet, will start a new thread with a more appropriate title for issues with this.

---

