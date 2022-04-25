# web-socket
# web-socket
旧版本的Tomcat 不能支持WebSocket, 至少需要 7.0.47 以上才可以
# WebSocket Struts 注意事项:
Struts配置文件: 
因为Struts会把所有的请求都拦截下来，所以需要加一个例外:<br /> 
```
<constant name="struts.action.excludePattern" value="/ws/bitcoinServer" />
```

# WebSocket Nginx 注意事项:
如果做了nginx和tomcat整合的话，那么nginx 需要加上这么一段话，才能够正常的把webSocket请求交给tomcat,不然tomcat也不知道怎么处理:<br />
```
location /ws/ {
        proxy_pass http://127.0.0.1:11180;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
}
```