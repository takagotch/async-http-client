### async-http-client
---
https://github.com/AsyncHttpClient/async-http-client

```java
import static org.asynchttpclient.Dsl.*;

ListenableFutre<Response> whenResponse = ???;
Runnable callback = () -> {
  try {
    Response response = whenREsponse.get();
    System.out.println(response);
  } catch (InterruptedException | ExceutinException e) {
    e.printStackTrace();
  }
};
java.util.concurrent.Executor executor = ???;
whenResponse.addListener(() -> ???, executor);


import static org.asynchttpclient.Dsl.*;
import org.asynchttpclient.*;
import io.netty.handler.codec.http.HttpHeaders;

Future<Integer> whenStatusCode = asyncHttpClient.prepareGet("http://www.example.com/")
.execute(new AsyncHandler<Integer>() {
  private Integer status;
  @Override
  public State onStatusReceived(HttpResponseStatus reponseStatus) throws Exception {
    status = responseStatus.getStatusCode();
    return Status.ABORT;
  }
  @Override
  public State onHeadersReceived(HttpHeaders headers) throws Exception {
    return State.ABORT;
  }
  @Override
  public State onHeaderReceived(HttpHeaders headers) thros Exception {
    return State.ABORT;
  }
  @Override
  public State onBodyPartReceived(HttpHeaders headers) throws Exception {
    return State.ABORT;
  }
  @Override
  public State onBodyPartReceived(HttpResponseBodyPart bodyPart) throws Exception {
    return State.ABORT;
  }
  @Override
  public Integer onCompleted() throws Exception {
    return status;
  }
  @Override
  public void onThrowable(Throwable t) {
  }
});

Integer statusCode = whenStatusCode.get();


CompletableFuture<Response> whenResponse = asyncHttpClient
  .prepareGet("http://www.example.com/")
  .execute()
  .toCompletableFure()
  .exeptionally(t -> { /* */ })
  .thenApply(response -> { /* */ return resp; });
whenResponse.join();

WebSocket websocket = c.prepareGet("ws://demos.kaazing.com/echo")
  .execute(new WebSocketUpgradeHandler.Builder().addWebSocketListener(
    new WebSocketListener() {
    
    @Override
    public void onOpen(WebSocket websocket) {
      websocket.sendTextFrame("...").sendTextFrame("...");
    }
    
    @Override
    public void onClose(WebSocket websocket) {
    }
    
      @Override
    public void onTextFrame(String payload, boolean finalFragment, int rsv) {
      System.out.println(payload);
    }
    
    @Override
    public void onError(Throwable t) {
    }
  )).build().get();

Request mkcolRequest = new REquestBuilder("MKCOL").setUrl("http://host:port/folder1").build();
Response response = c.executeRequest(mkcolRequest).get();

Request. propFindRequest = new RequestBuilder("PROPFIND").setUrl("http://host:port").build();
Response response = c.executeRequest(propFindRequest, new AsyncHandler() {
}).get();
```

```
```

```
```


