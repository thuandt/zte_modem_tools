# F670L / F671Y - Viettel

## Unlock full Telnet

```bash
# usage
poetry run python pwn.py -h
usage: pwn.py [-h] [-H HOST] [-u USER] [-p PASSWORD] -m MAC

ZTE modem factory mode exploit

options:
  -h, --help           show this help message and exit
  -H, --host HOST      router IP address (default: 192.168.1.1)
  -u, --user USER      login username (default: admin)
  -p, --pass PASSWORD  login password (default: admin)
  -m, --mac MAC        local machine MAC address, e.g. AA:BB:CC:DD:EE:FF

# install python dependencies
poetry install

# run exploit to get username & password
poetry run python pwn.py -H 192.168.1.1 -u admin -p admin -m <your_mac_address>


# login with random username & password
telnet 192.168.1.1
```

## Useful CLI Commands

### Check current region code
```bash
cat /userconfig/flag_type
```

### Get all available region codes
```bash
cat /etc/init.d/regioncode
```

### Change region code

```bash
upgradetest sdefconf 54 Viettel
upgradetest sdefconf 101 Viettel Campuchia
upgradetest sdefconf 56 VNPT
upgradetest sdefconf 198 Manufacture
upgradetest sdefconf 2008 FPT
```

If you have telnet access, but your shell is locked with `/bin/sh: Access Denied.`, you can use HEREDOC trick to bypass it. Remember to unplug PON connection first!

```bash
cat <<EOF >/userconfig/flag_type
current : 198
EOF
```

Now, you can access WebUI and upgrade to other firmware.

### Show all system current configuration

```bash
setmac show2
```

```txt
/ # setmac show2
===============Current Status of TagParam===============
    PONMAC[ID: 32769] is not set
   PONLOID[ID:  2180] is not set
 PONPASSWD[ID:  2181] is not set
    EPONSN[ID:  2182] is not set
       PSK[ID:  2183] is not set
  VENDORID[ID:  2176] is set to ZTEG
    GPONSN[ID:  2177] is set to D7017A31
   GPONPWD[ID:  2178] is set to XXXXXXXXX
    REG_ID[ID:  2179] is set to ZTEXXXXXXXXXXX
GPONPWDFLAG[ID:  2186] is not set
GPONHEXPWD[ID:  2187] is not set
       OUI[ID:   768] is set to XXXXXX
        SN[ID:   512] is set to XXXXXXXXXXX
      MAC1[ID:   256] is set to b0:8b:92:37:97:17
      MAC2[ID:   257] is set to b0:8b:92:37:97:18
      MAC3[ID:   258] is set to b0:8b:92:37:97:19
      MAC4[ID:   259] is set to b0:8b:92:37:97:1a
      MAC5[ID:   260] is set to b0:8b:92:37:97:1b
      MAC6[ID:   261] is set to b0:8b:92:37:97:1c
      MAC7[ID:   262] is set to b0:8b:92:37:97:1d
      MAC8[ID:   263] is set to b0:8b:92:37:97:1e
     SSID1[ID:  1024] is set to ZTE
     SSID2[ID:  1025] is set to ZTE_2.4G
     SSID3[ID:  1026] is set to ZTE_2.4G
     SSID4[ID:  1027] is set to ZTE_2.4G
     SSID5[ID:  1028] is set to ZTE_5G
     SSID6[ID:  1029] is set to ZTE_5G
     SSID7[ID:  1030] is set to ZTE_5G
     SSID8[ID:  1031] is set to ZTE_5G
WLAN0WEPKEY1[ID:  1280] is not set
WLAN0WEPKEY2[ID:  1281] is not set
WLAN0WEPKEY3[ID:  1282] is not set
WLAN0WEPKEY4[ID:  1283] is not set
WLAN1WEPKEY1[ID:  1284] is not set
WLAN1WEPKEY2[ID:  1285] is not set
WLAN1WEPKEY3[ID:  1286] is not set
WLAN1WEPKEY4[ID:  1287] is not set
WLAN2WEPKEY1[ID:  1288] is not set
WLAN2WEPKEY2[ID:  1289] is not set
WLAN2WEPKEY3[ID:  1290] is not set
WLAN2WEPKEY4[ID:  1291] is not set
WLAN3WEPKEY1[ID:  1292] is not set
WLAN3WEPKEY2[ID:  1293] is not set
WLAN3WEPKEY3[ID:  1294] is not set
WLAN3WEPKEY4[ID:  1295] is not set
   PSKKEY1[ID:  1296] is set to 88888888
   PSKKEY2[ID:  1297] is set to 88888888
   PSKKEY3[ID:  1298] is set to 88888888
   PSKKEY4[ID:  1299] is set to 88888888
WLAN4WEPKEY1[ID:  1312] is not set
WLAN4WEPKEY2[ID:  1313] is not set
WLAN4WEPKEY3[ID:  1314] is not set
WLAN4WEPKEY4[ID:  1315] is not set
WLAN5WEPKEY1[ID:  1316] is not set
WLAN5WEPKEY2[ID:  1317] is not set
WLAN5WEPKEY3[ID:  1318] is not set
WLAN5WEPKEY4[ID:  1319] is not set
WLAN6WEPKEY1[ID:  1320] is not set
WLAN6WEPKEY2[ID:  1321] is not set
WLAN6WEPKEY3[ID:  1322] is not set
WLAN6WEPKEY4[ID:  1323] is not set
WLAN7WEPKEY1[ID:  1324] is not set
WLAN7WEPKEY2[ID:  1325] is not set
WLAN7WEPKEY3[ID:  1326] is not set
WLAN7WEPKEY4[ID:  1327] is not set
   PSKKEY5[ID:  1328] is set to 88888888
   PSKKEY6[ID:  1329] is set to 88888888
   PSKKEY7[ID:  1330] is set to 88888888
   PSKKEY8[ID:  1331] is set to 88888888
WLANCALIBRATION[ID:  2053] is not set
  USERNAME[ID:  1537] is set to admin
 ADMINNAME[ID:  1538] is set to admin
USERPASSWD[ID:  1793] is set to ZTEXXXXXXXX
ADMINPASSWD[ID:  1794] is set to ZTEXXXXXXXX
VERSIONMODE[ID: 32770] is set to 5:F670L:V9.1:
   HLTMODE[ID:  2193] is not set
VoIPProtocolType[ID:  2054] is not set
   SOFTVER[ID: 36864] is set to V9.0.11P1NXX
   DsaNorm[ID:  2195] is set to <redacted>
   WANTYPE[ID: 40960] is not set
WANLOGICPORT[ID: 40961] is not set
MACLEARNENFLAG[ID:  4096] is not set
 ProductSn[ID:  2197] is not set
    rreset[ID:  2817] is set to 0
   AES_KEY[ID:  1824] is not set
FACTORY_PROCESSING[ID:  2816] is not set
  BOOT_NUM[ID:  3072] is not set
```

### Change default wifi configuration

With `ZTE` as SSID(s) and `88888888` as password

```bash
setmac 1 1024 ZTE        # SSID1
setmac 1 1025 <ZTE_2.4G> # SSID2
setmac 1 1026 <ZTE_2.4G> # SSID3
setmac 1 1027 <ZTE_2.4G> # SSID4
setmac 1 1028 ZTE_5G     # SSID5
setmac 1 1029 ZTE_5G     # SSID6
setmac 1 1030 ZTE_5G     # SSID7
setmac 1 1031 ZTE_5G     # SSID8
setmac 1 1296 88888888   # PSKKEY1
setmac 1 1297 88888888   # PSKKEY2
setmac 1 1298 88888888   # PSKKEY3
setmac 1 1299 88888888   # PSKKEY4
setmac 1 1328 88888888   # PSKKEY5
setmac 1 1329 88888888   # PSKKEY6
setmac 1 1330 88888888   # PSKKEY7
setmac 1 1331 88888888   # PSKKEY8
```

### Change username & password default

```bash
setmac 1 1537 admin        # USERNAME
setmac 1 1793 ZTEXXXXXXXXX # USERPASSWD

setmac 1 1538 admin        # ADMINNAME
setmac 1 1794 ZTEXXXXXXXXX # ADMINPASSWD
```

### Change SN PON

```bash
setmac 1 2176 ZTEG     # VENDORID
setmac 1 2177 D7017A31 # GPONSN

# reference only. may be it is not needed
# setmac 1 512 ZTEXXXXXXXXX # SN
# setmac 1 768 24A892       # OUI
# setmac 1 2178 XXXXXXXXX   # GPONPWD
```

### Change default MAC addresses

```bash
setmac 1 256 b0:8b:92:37:97:17 # MAC1
setmac 1 257 b0:8b:92:37:97:18 # MAC2
setmac 1 258 b0:8b:92:37:97:19 # MAC3
setmac 1 259 b0:8b:92:37:97:1A # MAC4
setmac 1 260 b0:8b:92:37:97:1B # MAC5
setmac 1 261 b0:8b:92:37:97:1C # MAC6
setmac 1 262 b0:8b:92:37:97:1D # MAC7
setmac 1 263 b0:8b:92:37:97:1E # MAC8
```

### Add bridge connection

```bash
sendcmd 1 DB set WANCPPP 0 HideListView 0
sendcmd 1 DB set WANCPPP 0 EnablePassThrough 1
sendcmd 1 DB save
```

### Disable TR069

It might not work as ISP (Viettel) can control it.

```bash
sendcmd 1 DB set MgtServer 0 Tr069Enable 0
sendcmd 1 DB set MgtServer 0 URL ""
sendcmd 1 DB set MgtServer 0 UserName ""
sendcmd 1 DB set MgtServer 0 PeriodicInformEnable 0
sendcmd 1 DB set MgtServer 0 PeriodicInformInterval 0
sendcmd 1 DB set MgtServer 0 SessionRetryTimes ""
sendcmd 1 DB set MgtServer 0 ConnectionRequestURL ""
sendcmd 1 DB set MgtServer 0 ConnectionRequestUsername ""
sendcmd 1 DB set MgtServer 0 ConnectionRequestPassword ""
sendcmd 1 DB save
```

### Enable telnet on LAN

```bash
sendcmd 1 DB p TelnetCfg
sendcmd 1 DB set TelnetCfg 0 Lan_Enable 1
sendcmd 1 DB set TelnetCfg 0 TS_UName admin
sendcmd 1 DB set TelnetCfg 0 TSLan_UName admin
sendcmd 1 DB set TelnetCfg 0 TS_UPwd ZTEXXXXXXXXX
sendcmd 1 DB set TelnetCfg 0 TSLan_UPwd ZTEXXXXXXXXX
sendcmd 1 DB set TelnetCfg 0 Max_Con_Num 99
sendcmd 1 DB set TelnetCfg 0 ExitTime 999999
sendcmd 1 DB set TelnetCfg 0 InitSecLvl 3
sendcmd 1 DB set TelnetCfg 0 CloseServerTime 9999999
sendcmd 1 DB set TelnetCfg 0 Lan_EnableAfterOlt 1
sendcmd 1 DB save
```

### Change LAN IP Address

```bash
sendcmd 1 DB set IPv4Address 0 IPAddress 192.168.88.1
sendcmd 1 DB set DHCP4sPool 0 MinAddress 192.168.88.2
sendcmd 1 DB set DHCP4sPool 0 MaxAddress 192.168.88.254
sendcmd 1 DB set DHCP4sPool 0 DNSServers1 192.168.88.1
sendcmd 1 DB set DHCP4sPool 0 IPRouters 192.168.88.1
sendcmd 1 DB save
```

### Add DHCP static reservations

```bash
sendcmd 1 DB addr DHCP4sStaticAddr
sendcmd 1 DB set DHCP4sStaticAddr 0 Enable 1
sendcmd 1 DB set DHCP4sStaticAddr 0 ViewName DEV.V4DP.Sr.Pl1.Bind1
sendcmd 1 DB set DHCP4sStaticAddr 0 Alias camera
sendcmd 1 DB set DHCP4sStaticAddr 0 Chaddr aa:bb:cc:dd:ee:ff
sendcmd 1 DB set DHCP4sStaticAddr 0 Yiaddr 192.168.88.1
sendcmd 1 DB save
```

## References

- [Hội Unlock Router/Mesh VN](https://t.me/unlockroutervoz)
- https://github.com/douniwan5788/zte_modem_tools/issues/20
- [ZTE F680 v4 hacking](https://orca.pet/ztef680v4/)
- https://github.com/mkst/zte-config-utility/
