# request-url
Increase the number of clicks on articles


```python
#!/usr/bin/python
import requests
import time
import random
from fake_useragent import UserAgent

url = 'http://webapi.http.zhimacangku.com/getip?num=400&type=1&pro=&city=0&yys=0&port=1&pack=221920&ts=0&ys=0&cs=0&lb=1&sb=0&pb=4&mr=1&regions=' #代理ip的api
r = requests.get(url)
ip_list= r.text.split( ) #split按空格切割，返回列表

ua = UserAgent() #实例化 UserAgent类
for i in range(1, 101):
    headers = {'User-Agent': ua.random}
    ip = random.choice(ip_list)
    proxies = {'http': 'http://{}'.format(ip),
               'https': 'htps://{}'.format(ip)}
    for j in range(1,23):
        url = f'http://www.jjwxc.net/onebook.php?novelid=6589291&chapterid={j}'
        r = requests.get(url=url, headers=headers, proxies=proxies)
        time.sleep(3)
        print(r)
        print(headers)
        print(ip)
        print(f'完成第{i}次 第{j}章点击')
```
