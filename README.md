

## Hystria V2


1. Installation
```
bash <(curl -fsSL https://get.hy2.sh/)
```

2. Certificate

```
mkdir hy2; cd hy2; openssl ecparam -genkey -name prime256v1 -out ca.key; openssl req -new -x509 -days 36500 -key ca.key -out ca.crt  -subj "/CN=bing.com"
```
3. Server Config
```
listen: :444
tls:
  cert: /root/hy2/ca.crt
  key: /root/hy2/ca.key
obfs:
  type: salamander
  salamander:
    password: efewEe5rQWE
auth:
  type: password
  password: efewEe5rQWE
quic:
  initStreamReceiveWindow: 8388608
  maxStreamReceiveWindow: 8388608
  initConnReceiveWindow: 20971520
  maxConnReceiveWindow: 20971520
  maxIdleTimeout: 60s
  maxIncomingStreams: 1024
  disablePathMTUDiscovery: false
bandwidth:
  up: 1 gbps
  down: 1 gbps
ignoreClientBandwidth: false
disableUDP: false
udpIdleTimeout: 60s
resolver:
  type: udp
  tcp:
    addr: 8.8.8.8:53
    timeout: 4s
  udp:
    addr: 8.8.4.4:53
    timeout: 4s
  tls:
    addr: 1.1.1.1:853
    timeout: 10s
    sni: cloudflare-dns.com
    insecure: false
  https:
    addr: 1.1.1.1:443
    timeout: 10s
    sni: cloudflare-dns.com
    insecure: false
```
4. Client Config
```
server: <IP>:444 
auth: efewEe5rQWE
transport:
  type: udp
  udp:
    hopInterval: 30s
obfs:
  type: salamander
  salamander:
    password: efewEe5rQWE
tls:
  sni: google.com 
  insecure: true 
bandwidth: 
  up: 20 mbps
  down: 100 mbps
quic:
  initStreamReceiveWindow: 8388608 
  maxStreamReceiveWindow: 8388608 
  initConnReceiveWindow: 20971520 
  maxConnReceiveWindow: 20971520 
  maxIdleTimeout: 30s 
  keepAlivePeriod: 10s 
  disablePathMTUDiscovery: false
fastOpen: true
lazy: true
socks5:
  listen: 192.168.50.176:1080
http:
  listen: 192.168.50.176:8080
```
# hiddify
```
sudo apt update && sudo apt install curl
sudo bash -c "$(curl -Lfo- https://raw.githubusercontent.com/hiddify/hiddify-config/main/common/download_install.sh)"
```
# X-UI Panel
```
bash <(curl -Ls https://raw.githubusercontent.com/alireza0/x-ui/master/install.sh)
```