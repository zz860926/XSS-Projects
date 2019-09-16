# 網站資安防護website-security
### 為金門大學 資訊工程學系 第五組
### 指導教授：柯志亨
### 組員：劉鳳安、陸佑函、蘇川民、王文濤、許哲瑋
## 一．專題動機
網路的時代有好的面向也有壞的面向，尤其是現代物聯網要崛起的時代。
我們的帳號和密碼到底怎麼被盜的呢?可能是"暴力破解"、"釣魚"、"封包竊取"等等可以竊取個資的方法，
我們應該要知道怎麼做防護，因為有可能因為一不小心的疏忽，讓自己的資訊被有心人士利用，所以我們要懂得怎麼保護自己的資訊，並且教導他人危機意識與防護的重要，
要怎麼做到呢？那就要在網站系統的Server上加一些防護機制，像是蜜罐誘導讓駭客困在陷阱中，又或是在防火牆上加些防護機制，等等手段來防止有心人士。
## 二．專題研究的攻擊方式
### 1.暴力破解
用Hydra套件來做暴力破解或字典攻擊，最主要是猜測帳號與密碼，把可能的選項一個個去試出來。  
主要以攻擊Webcam來做示範，可以看到設定Webcam時，要做登入的動作，所以我們猜測帳號與密碼，這樣我們就可以看到Webcam的影像。  
[暴力破解Webcam](https://github.com/NQUwebsecurityproject/website-security/blob/master/%E6%9A%B4%E5%8A%9B%E7%A0%B4%E8%A7%A3Webcam/README.md)
### 2.釣魚網站
 「網路釣魚」 （Phishing）即為透過"不明網站"來騙取個人資料的方式，最主要是騙取帳號與密碼用，可能以以下兩種方式做為網站的背景  
 1.使用與官網相似的網址與頁面（假網頁）  
 2.網路抽獎廣告連結  
 這裡有幾種建立釣魚網站的方式：  
 [Apache建簡易網站](https://github.com/NQUwebsecurityproject/website-security/tree/master/XSS%E6%94%BB%E6%93%8A/hackpasswd/hackerproof)  
 [beef建置釣魚網站]() 
### 3.DoS,DDoS
DoS攻擊：為阻斷服務攻擊，顧名思義就是想把伺服器的連線給阻斷掉，駭客通常會對伺服器一直做請求或偽造的回應封包，導致伺服器壅塞，這樣伺服器品質下滑。 
HPING3做資源消耗型攻擊，主要是TCP洪水攻擊，一直傳送大量帶有特定旗標的TCP(通常都是SYN)封包，導致受害者不斷回送ACK封包，使資料無法傳送。  
DDoS攻擊：為分散式阻斷服務攻擊，意思就是強化版的DoS攻擊，通常會運用兩個或以上的電腦去做攻擊，重點是又增加伺服器資源耗盡的問題，嚴重點還可能會讓伺服器當機。
## 三．防護機制
### 1.IPtable
Iptable是個控制Linux核心netfilter的模組，管理封包的處理與轉傳，所以其實是一個防火牆過濾的模組。  
可做上述的DoS、DDoS和暴力破解的防護。  
[DoS防護]()
### 2.Fail2ban
其實Fail2ban和IPtable的方式是一樣的，也是做防火牆過濾的作用，因為Fail2ban是建在IPtable上的套件，只是可以多增加一些設定，像是ssh,ftp連線的設定，寄送通知email的設定等等。  
可做上述DoS、DDoS和暴力破解的防護。  
[Fail2Ban 防範暴力破解(ssh、vsftp)](https://github.com/NQUwebsecurityproject/website-security/tree/master/Fail2Ban%20%E9%98%B2%E7%AF%84%E6%9A%B4%E5%8A%9B%E7%A0%B4%E8%A7%A3(ssh%E3%80%81vsftp))
### 3.二次認證
Google Authenticator就是google的二次認證套件，在你做遠端登入時可能你用的電腦被監控，或是其他惡意人士要竊取你遠端的帳密，這時再加一個像是即時安全鎖的機制，在你登完你的帳戶時，再用手機把你的即時密碼輸入進去，才能登到你的電腦裡。  
可做上述暴力破解的防護。  
[CentOS 7 SSH 連線驗證(Google Authenticator)](https://github.com/NQUwebsecurityproject/website-security/tree/master/google%E4%BA%8C%E6%AC%A1%E8%AA%8D%E8%AD%89(%E9%98%B2%E6%9A%B4%E5%8A%9B%E7%A0%B4%E8%A7%A3))
