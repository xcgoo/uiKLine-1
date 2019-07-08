# uiKLine
本工具用来显示交易信号csv
效果图：
![效果图](https://raw.githubusercontent.com/eachout/uiKLine/master/imgs/figure.png)

配合vnpy2.0+使用说明：
* 第一步： 确保vnpy已经安装成功。并参考本项目文件夹vnpy下的engine.py修改vnpy项目中vnpy/app/cta_backtester/engine.py：
        在run_backtesting函数中添加保存交易文件的代码：
                     
        trades = self.get_all_trades() 
        self.write_log('正在计算交易清单')
        self.calc_trades_pnl(trades,size,rate,slippage,interval)
        self.write_log('计算完成，正在写入交易结果文件')
        self.trade_to_csv(trades)
        self.write_log('交易文件保存完成')
        
    以及对应的calc_trades_pnl和trade_to_csv两个函数。
           
* 第二步：回测策略后生成trade_result.csv在vnpy的用户目录下（一般是/user/xxx/trade_result.csv）
         这时候可以修改csv第一行的interval列为想显示的K线，比如回测用的是1m数据，显示的时候想显示在小时图上，
         可以将第一行的interval改为60m，即可显示小时图K线。
         ![sample](https://raw.githubusercontent.com/eachout/uiKLine/master/imgs/sample_csv.png)
* 第三步：直接运行uiKLine.py即可，K线数据会自动从vnpy的database_manager数据库中调用。
