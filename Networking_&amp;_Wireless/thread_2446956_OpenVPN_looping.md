---
title: "OpenVPN looping"
date: 2020-07-09
forum: Networking &amp; Wireless
---

### Post by mlempenau on 2020-07-09
Open VPN tried to open but gets an error and then tries again.  I installed it about a week ago and it worked fine for about 5 days.  I need someone to help me understand what the syslog is telling me.  I have copied part of the log below.  I am using Ubuntu 20.04 which I upgraded about two weeks ago.  It's talking about a pid file that can't be found???  

ul  9 21:56:58 mlempenau20 systemd[1]: Starting OpenVPN connection to strongvpn...
Jul   9 21:56:58 mlempenau20 ovpn-strongvpn[62088]: Options error:  --writepid fails with '/run/openvpn/strongvpn.pid': No such file or  directory (errno=2)
Jul  9 21:56:58 mlempenau20 ovpn-strongvpn[62088]: Options error: --status fails with '/run/openvpn/strongvpn.status': No such file or directory (errno=2)
Jul  9 21:56:58 mlempenau20 ovpn-strongvpn[62088]: Options error: Please correct these errors.
Jul  9 21:56:58 mlempenau20 systemd[1]: [EMAIL="openvpn@strongvpn.service"]openvpn@strongvpn.service[/EMAIL]: Main process exited, code=exited, status=1/FAILURE
Jul  9 21:56:58 mlempenau20 ovpn-strongvpn[62088]: Use --help for more information.
Jul  9 21:56:58 mlempenau20 systemd[1]: [EMAIL="openvpn@strongvpn.service"]openvpn@strongvpn.service[/EMAIL]: Failed with result 'exit-code'.
Jul  9 21:56:58 mlempenau20 systemd[1]: Failed to start OpenVPN connection to strongvpn.
Jul  9 21:57:03 mlempenau20 systemd[1]: [EMAIL="openvpn@strongvpn.service"]openvpn@strongvpn.service[/EMAIL]: Scheduled restart job, restart counter is at 4.
Jul  9 21:57:03 mlempenau20 systemd[1]: Stopped OpenVPN connection to strongvpn.
Jul  9 21:57:03 mlempenau20 systemd[1]: Starting OpenVPN connection to strongvpn...
Jul   9 21:57:03 mlempenau20 ovpn-strongvpn[62107]: Options error:  --writepid fails with '/run/openvpn/strongvpn.pid': No such file or  directory (errno=2)
Jul  9 21:57:03 mlempenau20 ovpn-strongvpn[62107]: Options error: --status fails with '/run/openvpn/strongvpn.status': No such file or directory (errno=2)
Jul  9 21:57:03 mlempenau20 ovpn-strongvpn[62107]: Options error: Please correct these errors.
Jul  9 21:57:03 mlempenau20 ovpn-strongvpn[62107]: Use --help for more information.
Jul  9 21:57:03 mlempenau20 systemd[1]: [EMAIL="openvpn@strongvpn.service"]openvpn@strongvpn.service[/EMAIL]: Main process exited, code=exited, status=1/FAILURE
Jul  9 21:57:03 mlempenau20 systemd[1]: [EMAIL="openvpn@strongvpn.service"]openvpn@strongvpn.service[/EMAIL]: Failed with result 'exit-code'.
Jul  9 21:57:03 mlempenau20 systemd[1]: Failed to start OpenVPN connection to strongvpn.

---

